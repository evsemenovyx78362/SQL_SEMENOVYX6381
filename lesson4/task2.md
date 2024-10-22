# Базы данных и SQL. Обучение в записи
### Урок 4. Семинар: SQL – создание объектов, простые запросы выборки

Задание 2: Создание таблицы с авторами

Создайте таблицу (сущность) с авторами authors.

Перечень полей (атрибутов):

● id – числовой тип, автоинкремент, первичный ключ;

● name – строковый тип, обязательный к заполнению.

Заполните сущность authors данными из таблицы books.
```
DROP TABLE IF EXISTS authors;
CREATE TABLE authors (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(255) NOT NULL
);
INSERT INTO authors (name)
SELECT DISTINCT author
FROM books;
```