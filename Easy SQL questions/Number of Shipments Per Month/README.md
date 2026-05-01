# Number of Shipments Per Month

**[ENG]**

Write a query that will calculate the number of shipments per month. The unique key for one shipment is a combination of shipment_id and sub_id. Output the year_month in format YYYY-MM and the number of shipments in that month.

**[ES]**

Escribe una consulta que calcule el numero de envios por mes. La clave unica de un envio es una combinacion de shipment_id y sub_id. Salida el ano_mes en formato YYYY-MM y el numero de envios en ese mes.

### Table

## amazon_shipment

| shipment_id | sub_id | weight | shipment_date |
| ----------- | ------ | ------ | ------------- |
| 101         | 1      | 10     | 2021-08-30    |
| 101         | 2      | 20     | 2021-09-01    |
| 101         | 3      | 10     | 2021-09-05    |
| 102         | 1      | 50     | 2021-09-02    |
| 103         | 1      | 25     | 2021-09-01    |
| 103         | 2      | 30     | 2021-09-02    |
| 104         | 1      | 30     | 2021-08-25    |
| 104         | 2      | 10     | 2021-08-26    |
| 105         | 1      | 20     | 2021-09-02    |

# RESPUESTA

```sql
SELECT
    TO_CHAR(shipment_date, 'YYYY-MM') AS Ano_mes,
    COUNT(shipment_id + sub_id) AS total_shipments
FROM amazon_shipment
GROUP BY
    TO_CHAR(shipment_date, 'YYYY-MM')
```

# EXPLICACION

La consulta primero transforma `shipment_date` al formato `YYYY-MM` con `TO_CHAR`, ya que el resultado debe mostrarse por mes y ano en ese formato exacto. Eso hace que todas las filas del mismo periodo mensual compartan una misma etiqueta como `2021-08` o `2021-09`.

Una vez creada esa clave mensual, el `GROUP BY` junta los registros de cada mes y `COUNT(...)` calcula cuantas filas de envio hay en cada grupo. Como el enunciado aclara que la unicidad depende de `shipment_id` y `sub_id`, la idea es contar las ocurrencias de cada combinacion dentro del mes correspondiente para obtener el total mensual.
