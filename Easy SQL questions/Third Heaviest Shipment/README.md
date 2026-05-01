# Third Heaviest Shipment

**[ENG]**

You've been asked by Amazon to find the shipment_id and weight of the third heaviest shipment.
Output the shipment_id, and total_weight for that shipment_id.
In the event of a tie, do not skip ranks.

**[ESP]**

Te han pedido desde amazon encontrar el shipment_id y peso del tercer cargamento mas pesado. Muestra el shipment_id y el total_weight para ese shipment_id.
En el evento de empate no saltes los rankings.

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
    SELECT
        shipment_id,
        SUM(weight) AS total_weight
    FROM amazon_shipment
    GROUP BY
        shipment_id
),
ranking AS (
    SELECT
        *,
        DENSE_RANK() OVER(ORDER BY total_weight DESC) as rk
    FROM total
)
SELECT
    shipment_id,
    total_weight
FROM ranking
WHERE rk = 3
```

# EXPLICACION

La primera CTE, `total`, resume el peso total de cada envio sumando todas las filas que comparten el mismo `shipment_id`. Ese paso es necesario porque el ranking no se hace sobre cada pieza individual, sino sobre el peso acumulado de cada shipment completo.

Despues la CTE `ranking` aplica `DENSE_RANK()` ordenando `total_weight` de mayor a menor. Esta funcion es la adecuada porque, si hay empates, asigna el mismo rango sin saltarse posiciones posteriores. Por eso, al filtrar con `WHERE rk = 3`, obtenemos exactamente el tercer envio mas pesado respetando la regla del enunciado.
