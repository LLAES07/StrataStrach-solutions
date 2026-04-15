
# Customer Details

**[ENG]**
Find the details of each customer regardless of whether the customer made an order. Output the customer's first name, last name, and the city along with the order details. Sort records based on the customer's first name and the order details in ascending order.

**[ESP]**
Encuentra los detalles de cada cliente, independientemente de si el cliente realizó un pedido o no. Muestra el nombre, el apellido y la ciudad del cliente junto con los detalles del pedido. Ordena los registros según el nombre del cliente y los detalles del pedido en orden ascendente.


### Tables

customers

| id  | first_name | last_name | city          | address            | phone_number |
| --- | ---------- | --------- | ------------- | ------------------ | ------------ |
| 8   | John       | Joseph    | San Francisco |                    | 928-386-8164 |
| 7   | Jill       | Michael   | Austin        |                    | 813-297-0692 |
| 4   | William    | Daniel    | Denver        |                    | 813-368-1200 |
| 5   | Henry      | Jackson   | Miami         |                    | 808-601-7513 |
| 13  | Emma       | Isaac     | Miami         |                    | 808-690-5201 |
| 14  | Liam       | Samuel    | Miami         |                    | 808-555-5201 |
| 15  | Mia        | Owen      | Miami         |                    | 808-640-5201 |
| 1   | Mark       | Thomas    | Arizona       | 4476 Parkway Drive | 602-993-5916 |

orders


| id  | cust_id | order_date | order_details | total_order_cost |
| --- | ------- | ---------- | ------------- | ---------------- |
| 1   | 3       | 2019-03-04 | Coat          | 100              |
| 2   | 3       | 2019-03-01 | Shoes         | 80               |
| 3   | 3       | 2019-03-07 | Skirt         | 30               |
| 4   | 7       | 2019-02-01 | Coat          | 25               |
| 5   | 7       | 2019-03-10 | Shoes         | 80               |
| 6   | 15      | 2019-02-01 | Boats         | 100              |
| 7   | 15      | 2019-01-11 | Shirts        | 60               |
| 8   | 15      | 2019-03-11 | Slipper       | 20               |
| 9   | 15      | 2019-03-01 | Jeans         | 80               |
| 10  | 15      | 2019-03-09 | Shirts        | 50               |


# RESPUESTA

```sql



SELECT
    first_name,
    last_name,
    city,
    order_details
FROM customers c
LEFT JOIN orders o ON c.id = o.cust_id
ORDER BY 
    first_name ASC, order_details ASC;


```


# 📊 Explicación

Lo primero que solicitan es encontrar el detalle de todos los clientes aún cuando si no ha realizado una operación. Para esto necesitamos toda la tabla usuarios y hacer un `LEFT JOIN` con la tabla de pedidos.De esta forma tendremos a todos los usuarios aun cuando no hayan realizado una orden. Posteriormente al join realizamos el `ORDER BY` según lo solicitado y seleccionamos las columnas solicitadas.