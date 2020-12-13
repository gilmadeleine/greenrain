# SQL Practice from Data Prgoramming with Python_Udacity 

Query 1

SELECT f.title AS film_title, c.name AS category_name,          COUNT(rental_date)Rental_count
 FROM category c 
 JOIN film_category fc
    ON fc.category_id = c.category_id
 JOIN film f
   ON f.film_id = fc.film_id
 JOIN inventory i
   ON f.film_id = i.film_id
 JOIN rental r
   ON r.inventory_id = i.inventory_id
    WHERE c.name IN ('Animation', 'Children', 'Classics', 'Comedy', 'Family','Music')
GROUP BY 1,2
ORDER BY 1;

Query 2
SELECT r. rental_date, s.store_id, COUNT(rental_date) AS rental_count
  FROM rental r
  JOIN inventory i
    ON r.inventory_id= i.inventory_id
  JOIN store s
    ON s.store_id= i.store_id
 GROUP BY 1,2;

Query 3 

SELECT date, full_name, payment_total/payment_count AS per_count, payment_count, payment_total
FROM
    (SELECT DATE_TRUNC('month', p.payment_date)AS date, CONCAT(c.first_name,' ',  c.last_name)AS full_name, COUNT(p.payment_date)AS payment_count,SUM(p.amount)AS payment_total
   FROM payment p
     JOIN customer c
        ON c.customer_id= p.customer_id
  GROUP BY 1,2) t1
ORDER BY 3 DESC
LIMIT 10;
 
