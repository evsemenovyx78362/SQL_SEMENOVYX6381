# Базы данных и SQL. Обучение в записи
### Урок 10. Семинар: SQL – оконные функции


Задание 1: Получение заказов по сотруднику

Создайте хранимую процедуру GetEmployeeOrders, которая принимает
идентификатор сотрудника в качестве параметра и возвращает все заказы,
обработанные этим сотрудником.

В результате запроса будут столбцы:

● order_id: идентификатор заказа

● order_date: дата заказа


● customer_name: имя клиента
```
CREATE PROCEDURE GetEmployeeOrders(IN emp_id INT)
BEGIN
SELECT
o.order_id,
o.order_date,
c.customer_name
FROM
Orders o
JOIN
Customers c ON o.customer_id = c.customer_id
WHERE
o.employee_id = emp_id;
END;
CALL GetEmployeeOrders(1);
```
