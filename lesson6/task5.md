# Базы данных и SQL. Обучение в записи
### Урок 6. Семинар: SQL – выборка данных, сортировка, агрегатные функции

Задание 5: Сумма и количество заказов по клиентам

Выведите идентификатор клиента, имя клиента, сумму и количество его заказов.
Отсортируйте результат по идентификатору клиента.

```
SELECT
Customers.customer_id,
Customers.customer_name,
SUM(Orders.total_amount) AS total_amount,
COUNT(Orders.order_id) AS order_count
FROM Orders
JOIN Customers ON Orders.customer_id = Customers.customer_id
GROUP BY Customers.customer_id, Customers.customer_name
ORDER BY Customers.customer_id;
```