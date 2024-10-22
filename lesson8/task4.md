# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 4: Клиенты без заказов

Получите список всех клиентов, которые ничего не заказывали.
В результате запроса будет один столбец:

● customer_name: имя клиента
```
SELECT c.customer_name
FROM Customers c
LEFT JOIN Orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```
