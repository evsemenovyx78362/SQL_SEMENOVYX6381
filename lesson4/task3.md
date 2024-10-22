# Базы данных и SQL. Обучение в записи
### Урок 4. Семинар: SQL – создание объектов, простые запросы выборки

Задание 3: Добавление жанров и авторов в таблицу книг и вывод
книг по жанрам и авторам

Имеется таблица (сущность) с книгами books. У сущности имеются следующие поля
(атрибуты):

● id – идентификатор;

● title – название;

● author – автор;

● year – год издания;

● price – цена.

Создайте новые столбцы genre_id и author_id в таблице books и обновите
значения этих столбцов в соответствии с жанром и автором каждой книги:

```

ALTER TABLE books
ADD COLUMN genre_id INT,
ADD COLUMN author_id INT;

UPDATE books
SET genre_id = (SELECT id FROM genres WHERE name = 'Художественная
литература')
WHERE title IN ('Убить пересмешника', '1984', 'Великий Гэтсби', 'Над
пропастью во ржи', 'Моби Дик');
UPDATE books
SET genre_id = (SELECT id FROM genres WHERE name = 'Нехудожественная
литература')
WHERE title IN ('Скотный двор', 'Почти на Каталонии');
UPDATE books
SET genre_id = (SELECT id FROM genres WHERE name = 'Детектив')
WHERE title = 'Собака Баскервилей';
UPDATE books
SET genre_id = (SELECT id FROM genres WHERE name = 'Биография')
WHERE title = 'Дневник Анны Франк';
UPDATE books
SET genre_id = (SELECT id FROM genres WHERE name = 'Наука')
WHERE title = 'Краткая история времени';

UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Харпер Ли')
WHERE title = 'Убить пересмешника';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Джордж
Оруэлл')
WHERE title IN ('1984', 'Скотный двор', 'Почти на Каталонии');
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Ф. Скотт
Фицджеральд')
WHERE title = 'Великий Гэтсби';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Дж. Д.
Сэлинджер')
WHERE title = 'Над пропастью во ржи';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Герман
Мелвилл')
WHERE title = 'Моби Дик';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Артур Конан
Дойл')
WHERE title = 'Собака Баскервилей';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Анна Франк')
WHERE title = 'Дневник Анны Франк';
UPDATE books
SET author_id = (SELECT id FROM authors WHERE name = 'Стивен
Хокинг')
WHERE title = 'Краткая история времени';

SELECT b.title AS book_title, g.name AS genre_name, a.name AS
author_name
FROM books b
JOIN genres g ON b.genre_id = g.id
JOIN authors a ON b.author_id = a.id;
```