# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции


Задание 5: Аналитические функции для среднего, минимального и
максимального значения заказов

Используйте оконные функции для получения среднего, минимального и
максимального значения суммы заказов для каждого сотрудника.

В результате запроса будут столбцы:

● employee_name: имя сотрудника

● order_id: идентификатор заказа

● total_amount: сумма заказа

● avg_amount: средняя сумма заказа для каждого сотрудника

● min_amount: минимальная сумма заказа для каждого сотрудника

● max_amount: максимальная сумма заказа для каждого сотрудника
```
SELECT
e.employee_name,
o.order_id,
o.total_amount,
AVG(o.total_amount) OVER (PARTITION BY e.employee_id) AS
avg_amount,
MIN(o.total_amount) OVER (PARTITION BY e.employee_id) AS
min_amount,
MAX(o.total_amount) OVER (PARTITION BY e.employee_id) AS
max_amount
FROM
Employees e
JOIN
Orders o ON e.employee_id = o.employee_id;
```
