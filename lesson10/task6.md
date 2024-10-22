# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции



Задание 6: Комплексный анализ заказов

Создайте представление OrderAnalysis, которое будет содержать информацию о
каждом заказе, включая имя сотрудника, имя клиента, ранг заказа по сумме для
каждого сотрудника, среднюю, минимальную и максимальную сумму заказов для
каждого сотрудника, а также даты предыдущего и следующего заказов.

В результате запроса будут столбцы:

● employee_name: имя сотрудника

● customer_name: имя клиента

● order_id: идентификатор заказа

● total_amount: сумма заказа

● order_rank: ранг заказа по сумме для каждого сотрудника

● avg_amount: средняя сумма заказа для каждого сотрудника

● min_amount: минимальная сумма заказа для каждого сотрудника

● max_amount: максимальная сумма заказа для каждого сотрудника

● prev_order_date: дата предыдущего заказа

● next_order_date: дата следующего заказа
```
CREATE VIEW OrderAnalysis AS
SELECT
e.employee_name,
c.customer_name,
o.order_id,
o.total_amount,
RANK() OVER (PARTITION BY e.employee_id ORDER BY o.total_amount
DESC) AS order_rank,
AVG(o.total_amount) OVER (PARTITION BY e.employee_id) AS
avg_amount,
MIN(o.total_amount) OVER (PARTITION BY e.employee_id) AS
min_amount,
MAX(o.total_amount) OVER (PARTITION BY e.employee_id) AS
max_amount,
LAG(o.order_date) OVER (ORDER BY o.order_date) AS
prev_order_date,
LEAD(o.order_date) OVER (ORDER BY o.order_date) AS
next_order_date
FROM
Employees e
JOIN
Orders o ON e.employee_id = o.employee_id
JOIN
Customers c ON o.customer_id = c.customer_id;
SELECT * FROM OrderAnalysis;
```