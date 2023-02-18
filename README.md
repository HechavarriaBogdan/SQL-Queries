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

Выберает все заказы, где есть хотя бы один товар - «гречка» и время доставки свыше 30 минут. В результирующей таблице выводятся ID заказов и ID курьеров.

SELECT

        ORDERS_ID,
        EMPLOYEE_ID
FROM

        Orders
WHERE

        ITEMS LIKE '%гречка%' AND DELIVERY_TIME > 30;