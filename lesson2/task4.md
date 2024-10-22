# Базы данных и SQL. Обучение в записи
### Урок 2. Семинар: Установка СУБД, подключение к БД, просмотр и создание таблиц

Задание 4*: Анализ и статистика по книгам

Имеется таблица (сущность) с книгами books. У сущности имеются
следующие поля (атрибуты):

● id – идентификатор;

● title – название;

● author – автор;

● year – год издания;

● price – цена.

Необходимо выполнить следующие задачи:
1. Подсчитать общее количество книг в таблице.
2. Найти среднюю цену книг.
3. Вывести автора, у которого самая дорогая книга.
4. Подсчитать количество книг для каждого автора и вывести
авторов, у которых более одной книги.
5. Найти книги, изданные до 1950 года, и вывести их названия и
авторов в алфавитном порядке авторов.

```

SELECT COUNT(*) AS total_books
FROM books;

SELECT AVG(price) AS average_price
FROM books;

SELECT author
FROM books
WHERE price = (SELECT MAX(price) FROM books);

SELECT author, COUNT(*) AS book_count
FROM books
GROUP BY author
HAVING COUNT(*) > 1;

SELECT title, author
FROM books
WHERE year < 1950
ORDER BY author;
```