# Домашнее задание к занятию "`Индексы`" - `Андрющенко Вячеслав`


---

### Задание 1  

Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

### Решение 1  


![Индексы](/img/1.png)  


 


### Задание 2  

Выполните explain analyze следующего запроса:

select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id

перечислите узкие места;

оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.



### Решение 2 


Узкие места:

1) Нужно добавить джоины

2) Добавить индексы

4) При обработке через distinct большие затраты при проверке уникальности

![Добавление индексов](/img/2.png)  


![Оптимизированный запрос](/img/2_1.png)   


![EXPLAIN](/img/2_2.png)  


