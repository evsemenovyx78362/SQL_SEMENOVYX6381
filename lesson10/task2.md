# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции


Задание 2: Создание представления для суммы заказов по сотрудникам

Создайте представление EmployeeOrderSummary, которое покажет общую сумму
заказов для каждого сотрудника.

В результате запроса будут столбцы:

● employee_name: имя сотрудника

● total_sales: общая сумма заказов
```
CREATE VIEW EmployeeOrderSummary AS
SELECT
e.employee_name,
SUM(o.total_amount) AS total_sales
FROM
Employees e
JOIN
Orders o ON e.employee_id = o.employee_id
GROUP BY
e.employee_name;
SELECT * FROM EmployeeOrderSummary;
```

