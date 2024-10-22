# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 2: Заказы от определенных перевозчиков

Получите список всех заказов, разделив их на те, которые были доставлены
перевозчиком 'СДЕК', и те, которые были доставлены другими перевозчиками.

В результате запроса будут столбцы:
● order_id: идентификатор заказа
● customer_id: идентификатор клиента
● order_date: дата заказа
● shipper_name: имя перевозчика
```
SELECT
order_id,
customer_id,
order_date,
total_amount,
CASE
WHEN shipper_id = (SELECT shipper_id FROM Shippers WHERE
shipper_name = 'СДЕК')
THEN 'Доставлено СДЕК'
ELSE 'Доставлено другим перевозчиком'
END AS delivery_status
FROM
Orders;
```
