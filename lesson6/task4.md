# Базы данных и SQL. Обучение в записи
### Урок 6. Семинар: SQL – выборка данных, сортировка, агрегатные функции

Задание 4: Количество заказов по категориям книг
Выведите категорию книг и количество заказов, которые содержат книги этой
категории. Показать только те категории, которые имеют больше одного заказа.

```SELECT
Categories.category_name,
COUNT(DISTINCT Orders.order_id) AS order_count
FROM OrderDetails
JOIN Products ON OrderDetails.product_id = Products.product_id
JOIN Categories ON Products.category_id = Categories.category_id
JOIN Orders ON OrderDetails.order_id = Orders.order_id
GROUP BY Categories.category_name
HAVING COUNT(DISTINCT Orders.order_id) > 1;```
