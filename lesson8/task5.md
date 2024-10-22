# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 5: Заказы с высокой стоимостью

Создайте новую таблицу HighValueOrders, которая будет содержать заказы на
сумму более 500. Включите идентификатор заказа, идентификатор клиента и сумму
заказа.

В результате запроса будут столбцы:

● order_id: идентификатор заказа

● customer_id: идентификатор клиента

● total_amount: сумма заказа

```

CREATE TABLE HighValueOrders (
order_id INT,
customer_id INT,
total_amount DECIMAL(10, 2)
);

INSERT INTO HighValueOrders (order_id, customer_id, total_amount)
SELECT
order_id,
customer_id,
total_amount
FROM
Orders
WHERE
total_amount > 500;

SELECT * FROM HighValueOrders;
```
