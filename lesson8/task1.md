# Базы данных и SQL. Обучение в записи
### Урок 8. Семинар: SQL – работа с несколькими таблицами

Задание 1: Список всех книг с количеством заказов

Получите список всех книг вместе с именем автора, категорией и количеством заказов
каждой книги.

В результате запроса будут столбцы:
● product_name: название книги
● author: имя автора
● category_name: название категории
● order_count: количество заказов этой книги

```SELECT
p.product_name,
p.author,
c.category_name,
COUNT(od.order_id) AS order_count
FROM
Products p
INNER JOIN
Categories c ON p.category_id = c.category_id
LEFT JOIN
OrderDetails od ON p.product_id = od.product_id
GROUP BY
p.product_name, p.author, c.category_name;
```
