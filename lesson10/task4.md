# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции

Задание 4: Получение предыдущего и следующего заказа для каждого заказа

Используйте оконные функции для получения предыдущего и следующего заказа для
каждого заказа на основе даты заказа.

В результате запроса будут столбцы:

● order_id: идентификатор заказа

● order_date: дата заказа

● prev_order_date: дата предыдущего заказа

● next_order_date: дата следующего заказа
```
SELECT
order_id,
order_date,
LAG(order_date) OVER (ORDER BY order_date) AS prev_order_date,
LEAD(order_date) OVER (ORDER BY order_date) AS next_order_date
FROM
Orders;
```