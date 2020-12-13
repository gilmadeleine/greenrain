# SQL Practice Question 


Query 2
SELECT r. rental_date, s.store_id, COUNT(rental_date) AS rental_count
  FROM rental r
  JOIN inventory i
    ON r.inventory_id= i.inventory_id
  JOIN store s
    ON s.store_id= i.store_id
 GROUP BY 1,2;


 
