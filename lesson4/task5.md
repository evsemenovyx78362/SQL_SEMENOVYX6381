# Базы данных и SQL. Обучение в записи
### Урок 4. Семинар: SQL – создание объектов, простые запросы выборки

Задание 5: Выборка книг по средней цене жанра

Имеется таблица (сущность) с книгами books и таблица с жанрами genres. У
сущностей имеются следующие поля (атрибуты):

● books.id – идентификатор;

● books.title – название;

● books.author – автор;

● books.year – год издания;

● books.price – цена;

● books.genre_id – идентификатор жанра;

● genres.id – идентификатор;

● genres.name – название жанра.

Необходимо вывести название жанра и среднюю цену книг в этом жанре для жанров,
где средняя цена выше 300.

```
SELECT genres.name AS genre, AVG(books.price) AS average_price
FROM books
JOIN genres ON books.genre_id = genres.id
GROUP BY genres.name
HAVING AVG(books.price) > 300;
```