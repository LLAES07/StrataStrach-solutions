# Weight For First Shipment

**[ENG]**

Write a query to find the weight for each shipment's earliest shipment date. Output the shipment id along with the weight.

**[ESP]**

Escriba una consulta para encontrar el peso de la fecha de envio mas temprana de cada envio. Genere la identificacion del envio junto con el peso.

### TABLA

amazon_shipment

|shipment_id|sub_id|weight|shipment_date|
|---|---|---|---|
|101|1|10|2021-08-30|
|101|2|20|2021-09-01|
|101|3|10|2021-09-05|
|102|1|50|2021-09-02|
|103|1|25|2021-09-01|
|103|2|30|2021-09-02|
|104|1|30|2021-08-25|
|104|2|10|2021-08-26|
|105|1|20|2021-09-02|

# RESPUESTA

```sql
WITH earliest_shipments AS (
    SELECT 
        shipment_id, 
        MIN(shipment_date) as early_date
    FROM amazon_shipment
    GROUP BY shipment_id
)
SELECT 
    s.shipment_id, 
    SUM(s.weight) AS total_weight
FROM amazon_shipment s
JOIN earliest_shipments e 
  ON s.shipment_id = e.shipment_id 
  AND s.shipment_date = e.early_date
GROUP BY s.shipment_id;
```

# EXPLICACION

La CTE `earliest_shipments` obtiene la fecha minima de envio para cada `shipment_id`, lo que permite identificar cual fue el primer registro de cada envio. Ese paso separa claramente la busqueda de la fecha inicial del calculo final del peso.

Luego la tabla original se une con esa CTE por `shipment_id` y por la fecha minima encontrada. Asi solo permanecen las filas que corresponden al primer envio de cada grupo. Finalmente, `SUM(s.weight)` devuelve el peso asociado a esa fecha inicial, lo cual resulta util si para un mismo envio hubiera mas de una fila en la fecha mas temprana.
