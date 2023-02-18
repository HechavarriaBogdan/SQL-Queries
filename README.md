## Entity-relationship diagram

![Header](https://github.com/HechavarriaBogdan/SQL-Queries/blob/main/assets/diploma-333.png)

## Initial data
Orders —  все доставленные заказы;
ORDERS_ID — ID заказов, int;
USER_ID — ID пользователей, int;
EMPLOYEE_ID — ID сотрудников, int;
DELIVERY_TIME — время доставки в минутах, int;
ITEMS — список товаров, char;

Users — пользователи;
USER_ID — ID пользователей, int;
FULL_NAME — полное ФИО пользователя, char;
PHONE — номер телефона пользователя, char;
ADDRESS — адрес пользователя, char;

Employees — работники;
EMPLOYEE_ID — ID сотрудника, int;
FIRST_NAME —имя сотрудника, char;
LAST_NAME — фамилия сотрудника, char;
PHONE — телефон сотрудника, char;
JOB_ID — ID специализации, int;

Jobs — типы работ в сервисе
JOB_ID — ID специализации, int;
JOB_TYPE — тип специализации, char;
HOURS — число рабочих часов в неделю, int;
SALARY — зарплата сотрудника с данной специализацией в рублях, int;

## SQL Queries

### 1

Выберает все заказы, где есть хотя бы один товар - «гречка» и время доставки свыше 30 минут. В результирующей таблице выводятся ID заказов и ID курьеров.

    SELECT
        ORDERS_ID,
        EMPLOYEE_ID
    FROM
        Orders
    WHERE
        ITEMS LIKE '%гречка%' AND DELIVERY_TIME > 30;

### 2
Выбирает пять самых активных клиентов по количеству заказов. 
В результирующую таблицу выводится ID каждого пользователя и число заказов. 
Отсортировываются данные по убыванию числа заказов, выбирается пять самых активных клиентов.

    SELECT
        USER_ID,
        COUNT(ORDERS_ID) AS cnt_orders
    FROM
        orders
    GROUP BY
        USER_ID
    ORDER BY
        cnt_orders DESC
    LIMIT
        5;

### 3
Выводит список ID всех сотрудников, у которых в специализации содержится «менеджер», с зарплатой больше 70 000 рублей.

    SELECT
        Employees.EMPLOYEE_ID AS EMPLOYEE_ID,
        Jobs.JOB_TYPE AS JOB_TYPE,
        Jobs.SALARY AS SALARY
    FROM
        Employees
    INNER JOIN Jobs ON Employees.JOB_ID = Jobs.JOB_ID 
    WHERE
        Jobs.JOB_TYPE LIKE '%менеджер%'
        AND Jobs.SALARY > 70000;