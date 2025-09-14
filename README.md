# Домашнее задание к занятию "`Индексы`" - `Лоскутов Вячеслав`

### Задание 1

Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

### Ответ:

```
SELECT 
    ROUND(
        (SUM(index_length) * 100.0 / SUM(data_length + index_length)), 
        2
    ) AS percent_index_to_table
FROM 
    information_schema.tables
WHERE 
    table_schema = 'sakila';
```
![percent](https://github.com/NightWalkerZ488/hw_indexes_lvv/blob/main/1.PNG)

### Задание 2

Выполните explain analyze следующего запроса:
```sql
select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
```
- перечислите узкие места;
- оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.

### Ответ:



