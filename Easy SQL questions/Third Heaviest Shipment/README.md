# Third Heaviest Shipment

**[ENG]**

You've been asked by Amazon to find the shipment_id and weight of the third heaviest shipment.
Output the shipment_id, and total_weight for that shipment_id.
In the event of a tie, do not skip ranks.

**[ESP]**

Te han pedido desde amazon encontrar el shipment_id y peso de el 3 cargamento más pesado. Muestra el shipment_id, and total_weiht para ese shipment_id.
En el evento de empate no saltes los rankings

### TABLA

amazon_shipment| shipment_id | sub_id | weight | shipment_date |
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

WITH total AS (
    -- Calcula el total de peso por id
    SELECT
        shipment_id,
        SUM(weight) AS total_weight
    FROM amazon_shipment
    GROUP BY
        shipment_id
),

ranking AS (

    -- Genera un ranking en empates comparten el mismo rankinh
    SELECT
        *,
        DENSE_RANK() OVER(ORDER BY total_weight DESC) as rk
    FROM total
    
)

SELECT
    -- Query final
    shipment_id,
    total_weight
FROM ranking
WHERE rk = 3
    


```