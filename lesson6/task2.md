# Базы данных и SQL. Обучение в записи
### Урок 6. Семинар: SQL – выборка данных, сортировка, агрегатные функции

Задание 2: Количество заказов по перевозчикам

Выведите имя перевозчика, месяц и год заказа, а также количество уникальных
заказов, доставленных каждым перевозчиком в каждый месяц и год.


```
SELECT
Shippers.shipper_name,
EXTRACT(YEAR FROM Orders.order_date) AS year,
EXTRACT(MONTH FROM Orders.order_date) AS month,
COUNT(DISTINCT Orders.order_id) AS unique_orders_count
FROM Orders
JOIN Shippers ON Orders.shipper_id = Shippers.shipper_id
GROUP BY
Shippers.shipper_name,
EXTRACT(YEAR FROM Orders.order_date),
EXTRACT(MONTH FROM Orders.order_date);
```
