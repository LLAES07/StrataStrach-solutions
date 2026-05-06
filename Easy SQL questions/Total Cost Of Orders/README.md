# Total Cost Of Orders


# ðŸ“Œ PROBLEMA

**[ENG]**

Find the total cost of each customer's orders. Output customer's id, first name, and the total order cost. Order records by customer's first name alphabetically.

**[ESP]**

Encuentra el costo total de cada orden de los clientes. Muestra la id del cliente, el primer nombre, y el costo total de la orden. Ordena los registros segÃºn el nombre del cliente alfabÃ©ticamente.



# TABLA

**customers**

| id | first_name | last_name | city          | address              | phone_number |
| -- | ---------- | --------- | ------------- | -------------------- | ------------ |
| 8  | John       | Joseph    | San Francisco |                      | 928-386-8164 |
| 7  | Jill       | Michael   | Austin        |                      | 813-297-0692 |
| 4  | William    | Daniel    | Denver        |                      | 813-368-1200 |
| 5  | Henry      | Jackson   | Miami         |                      | 808-601-7513 |
| 13 | Emma       | Isaac     | Miami         |                      | 808-690-5201 |
| 14 | Liam       | Samuel    | Miami         |                      | 808-555-5201 |
| 15 | Mia        | Owen      | Miami         |                      | 808-640-5201 |
| 1  | Mark       | Thomas    | Arizona       | 4476 Parkway Drive   | 602-993-5916 |
| 12 | Eva        | Lucas     | Arizona       | 4379 Skips Lane      | 301-509-8805 |
| 6  | Jack       | Aiden     | Arizona       | 4833 Coplin Avenue   | 480-303-1527 |
| 2  | Mona       | Adrian    | Los Angeles   | 1958 Peck Court      | 714-409-9432 |
| 10 | Lili       | Oliver    | Los Angeles   | 3832 Euclid Avenue   | 530-695-1180 |
| 3  | Farida     | Joseph    | San Francisco | 3153 Rhapsody Street | 813-368-1200 |
| 9  | Justin     | Alexander | Denver        | 4470 McKinley Avenue | 970-433-7589 |
| 11 | Frank      | Jacob     | Miami         | 1299 Randall Drive   | 808-590-5201 |


**orders**

| id | cust_id | order_date | order_details | total_order_cost |
| -- | ------- | ---------- | ------------- | ---------------- |
| 1  | 3       | 2019-03-04 | Coat          | 100              |
| 2  | 3       | 2019-03-01 | Shoes         | 80               |
| 3  | 3       | 2019-03-07 | Skirt         | 30               |
| 4  | 7       | 2019-02-01 | Coat          | 25               |
| 5  | 7       | 2019-03-10 | Shoes         | 80               |
| 6  | 15      | 2019-02-01 | Boats         | 100              |
| 7  | 15      | 2019-01-11 | Shirts        | 60               |
| 8  | 15      | 2019-03-11 | Slipper       | 20               |
| 9  | 15      | 2019-03-01 | Jeans         | 80               |
| 10 | 15      | 2019-03-09 | Shirts        | 50               |
| 11 | 5       | 2019-02-01 | Shoes         | 80               |
| 12 | 12      | 2019-01-11 | Shirts        | 60               |
| 13 | 12      | 2019-03-11 | Slipper       | 20               |
| 14 | 4       | 2019-02-01 | Shoes         | 80               |
| 15 | 4       | 2019-01-11 | Shirts        | 60               |
| 16 | 3       | 2019-04-19 | Shirts        | 50               |
| 17 | 7       | 2019-04-19 | Suit          | 150              |
| 18 | 15      | 2019-04-19 | Skirt         | 30               |
| 19 | 15      | 2019-04-20 | Dresses       | 200              |
| 20 | 12      | 2019-01-11 | Coat          | 125              |
| 21 | 7       | 2019-04-01 | Suit          | 50               |
| 22 | 7       | 2019-04-02 | Skirt         | 30               |
| 23 | 7       | 2019-04-03 | Dresses       | 50               |
| 24 | 7       | 2019-04-04 | Coat          | 25               |
| 25 | 7       | 2019-04-19 | Coat          | 125              |
| 26 | 3       | 2019-04-20 | Gloves        | 20               |
| 27 | 3       | 2019-04-21 | Tie           | 25               |
| 28 | 3       | 2019-04-22 | Cap           | 15               |
| 29 | 3       | 2019-04-23 | Jacket        | 120              |
| 30 | 1       | 2019-04-19 | Jacket        | 150              |
| 31 | 1       | 2019-04-19 | Shoes         | 125              |

# ðŸ’» REPSUESTA

```sql

SELECT
    c.id,
    c.first_name,
    COALESCE(SUM(o.total_order_cost), 0) AS costo_total_orden
FROM customers c
LEFT JOIN orders o
ON c.id = o.cust_id
GROUP BY 
    c.id,
    c.first_name
ORDER BY 2 ASC;


```

# ðŸ§  EXPLICACIÃ“N

Necesitamos conocer el total de orden por ide cada usuario. Por esta razon generaremos un LEFT JOIN entre la tabla `customers` de esta manera tendrÃ¡ todos los ususarios conectando esta con `orders` asÃ­ traemos cada orden correspondiente a cada usuario. Posterior utilizamos GROUP BY para juntar todos los registros de cada usuario sumando la columna `total_order_cost` utilizanto `COALESCE` para incluir a los usuarios que no tengan ordenes.
## EXPLICACION

`SUM(order_total)` agrega todos los valores de las ordenes en una sola cifra. Es la forma mas directa de obtener el costo total.

Cuando se combina con el `JOIN`, cada cliente queda asociado a sus pedidos antes de sumar. Asi el resultado refleja el gasto acumulado por usuario y no solo el total general de la tabla.
