# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции


Задание 3: Использование оконных функций для ранжирования заказов

Ранжируйте заказы каждого сотрудника на основе суммы заказа (total_amount).

В результате запроса будут столбцы:

● employee_name: имя сотрудника

● order_id: идентификатор заказа

● total_amount: сумма заказа

● order_rank: ранг заказа по сумме для каждого сотрудника
```
SELECT
e.employee_name,
o.order_id,
o.total_amount,
RANK() OVER (PARTITION BY e.employee_id ORDER BY o.total_amount
DESC) AS order_rank
FROM
Employees e
JOIN
Orders o ON e.employee_id = o.employee_id;
```