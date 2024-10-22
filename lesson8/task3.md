# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 3: Количество заказов у каждого клиента

Получите список всех клиентов и количество их заказов. Включите клиентов, которые
не делали заказов.

В результате запроса будут столбцы:
● customer_name: имя клиента
● order_count: количество заказов
```
SELECT
c.customer_name,
COUNT(o.order_id) AS order_count
FROM
Customers c
LEFT JOIN
Orders o ON c.customer_id = o.customer_id
GROUP BY
c.customer_name;
```
