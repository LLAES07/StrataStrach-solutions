# Customer Revenue In March


**[ENG]**

Calculate the total revenue from each customer in March 2019. Include only customers who were active in March 2019. An active user is a customer who made at least one transaction in March 2019.

Output the revenue along with the customer id and sort the results based on the revenue in descending order.


**[ESP]**

Calcula el total de ingresos de cada cliente para marzo de 2019. Incluye solamente clientes que fueron activos en marzo de 2019. Un usuario activo es un cliente que hizo al menos una transacción en marzo de 2019.

Muestra el ingreso total junto al id del cliente y ordena los resultados según el ingreso en orden descendente.



### Table

orders


|id|cust_id|order_date|order_details|total_order_cost|
|---|---|---|---|---|
|1|3|2019-03-04|Coat|100|
|2|3|2019-03-01|Shoes|80|
|3|3|2019-03-07|Skirt|30|
|4|7|2019-02-01|Coat|25|
|5|7|2019-03-10|Shoes|80|
|6|15|2019-02-01|Boats|100|
|7|15|2019-01-11|Shirts|60|
|8|15|2019-03-11|Slipper|20|
|9|15|2019-03-01|Jeans|80|
|10|15|2019-03-09|Shirts|50|
|11|5|2019-02-01|Shoes|80|
|12|12|2019-01-11|Shirts|60|
|13|12|2019-03-11|Slipper|20|
|14|4|2019-02-01|Shoes|80|
|15|4|2019-01-11|Shirts|60|
|16|3|2019-04-19|Shirts|50|
|17|7|2019-04-19|Suit|150|
|18|15|2019-04-19|Skirt|30|
|19|15|2019-04-20|Dresses|200|
|20|12|2019-01-11|Coat|125|
|21|7|2019-04-01|Suit|50|
|22|7|2019-04-02|Skirt|30|
|23|7|2019-04-03|Dresses|50|
|24|7|2019-04-04|Coat|25|
|25|7|2019-04-19|Coat|125|
|26|3|2019-04-20|Gloves|20|
|27|3|2019-04-21|Tie|25|
|28|3|2019-04-22|Cap|15|
|29|3|2019-04-23|Jacket|120|
|30|1|2019-04-19|Jacket|150|
|31|1|2019-04-19|Shoes|125|


# RESPUESTA

```sql

SELECT 
    cust_id,
    -- Suma el total de la orden para cada cliente
    SUM(total_order_cost) AS total_revenue
FROM orders
WHERE
    -- Filtra por año y por mes
    EXTRACT(YEAR FROM order_date) = '2019' AND
    EXTRACT(MONTH FROM order_date) = 03
GROUP BY
    -- Agrupa por cliente
    cust_id
ORDER BY total_revenue DESC;


```
