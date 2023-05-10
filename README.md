# My-first-SQL-project.

-- 1
SELECT * FROM sakila.payment;
use sakila;
select amount from payment 
where amount > 2;

-- 2
select title, replacement_cost 
from film
where replacement_cost <10 and rating= 'PG';

-- 3
select * from film;
select cast(avg(rental_rate) as decimal(5,2)) as Average_Rentals
from film
where rating in('pg', 'g', 'NC', 'g');

-- 4
select * from customer;
select first_name, length(first_name) as Lenght_of_name
from customer;

-- 5
select * from film;
select locate('e', description) as Location from film;

-- 6
select * from film;
select rating, sum(length) from film
group by rating
having sum(length) > 22000;

-- 7
select * from film;

select description, length(description) as Length_description,
case 
   when Length_description in ('a') then 'oo'
   end  from film;

with Length_description as 
(
select title, release_year,
 release_year - rental_duration as durat from film
),
	Length_descriptions2 as 
(
select title, rental_rate, 
rental_duration as durat from film
)
select title, le1.durat, release_year from Length_description le1
 join Length_descriptions2 as le2 using (title);

select avg(durat) from Length_description;











