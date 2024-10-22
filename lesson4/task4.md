# Базы данных и SQL. Обучение в записи
### Урок 4. Семинар: SQL – создание объектов, простые запросы выборки

Задание 4: Обновление цен на книги

Имеется таблица (сущность) с книгами books. У сущности имеются следующие поля
(атрибуты):

● id – идентификатор;

● title – название;

● author – автор;

● year – год издания;

● price – цена.

Необходимо увеличить цену на все книги, изданные до 2000 года, на 10%.
```
UPDATE books
SET price = price * 1.10
WHERE year < 2000;
```