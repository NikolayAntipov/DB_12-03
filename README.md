# Домашнее задание к занятию «SQL. Часть 1» - Антипов Н.С.

## Задание 1
Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

```sql
select distinct district
from sakila.address
where  district like 'K%a'
and position(' ' in district) = 0;
```

## Задание 2
Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

```sql
select  amount, payment_date
from  sakila.payment
where  Date(payment_date) between '2005-06-15' and '2005-06-18'
and amount > 10.0;
```

## Задание 3
Получите последние пять аренд фильмов.

```sql
select *
from sakila.rental
order by rental_date desc
limit 5;
```

## Задание 4
Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
замените буквы 'll' в именах на 'pp'.

```sql
select replace(lower(first_name), 'll', 'pp'), lower(last_name), active
from sakila.customer
where first_name in ('Kelly', 'Willie') and active = 1;
```
