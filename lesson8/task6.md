# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 6: Анализ продаж книг по категориям

Получите список всех категорий книг с суммой продаж, средней ценой книги,
минимальной и максимальной ценой книги, а также количеством уникальных заказов.
Отсортируйте по сумме продаж в порядке убывания и ограничьте результат первыми 5
строками.

В результате запроса будут столбцы:

● category_name: название категории

● total_sales: общая сумма продаж

● avg_price: средняя цена книги

● min_price: минимальная цена книги

● max_price: максимальная цена книги

● unique_orders: количество уникальных заказов
```
SELECT
c.category_name,
SUM(od.quantity * p.price) AS total_sales,
AVG(p.price) AS avg_price,
MIN(p.price) AS min_price,
MAX(p.price) AS max_price,
COUNT(DISTINCT od.order_id) AS unique_orders
FROM
Categories c
JOIN
Products p ON c.category_id = p.category_id
JOIN
OrderDetails od ON p.product_id = od.product_id
GROUP BY
c.category_name
ORDER BY
total_sales DESC
LIMIT 5;
```