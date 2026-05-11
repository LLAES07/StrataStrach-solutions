# Customer Average Orders

## PROBLEMA

**[ENG]**
How many customers placed an order and what is the average order amount?

**[ESP]**
Cuantos clientes realizaron una orden y cual es el monto promedio de esas ordenes.

---

### TABLA

`postmates_orders`

|customer_id|courier_id|seller_id|order_timestamp_utc|amount|city_id|
|---|---|---|---|---|---|
|1|102|224|79|2019-03-11 23:27:00|155.73|
|2|104|224|75|2019-04-11 04:24:00|216.6|
|3|100|239|79|2019-03-11 21:17:00|168.69|
|4|101|205|79|2019-03-11 02:34:00|210.84|
|5|103|218|71|2019-04-11 00:15:00|212.6|
|6|102|201|77|2019-03-11 18:22:00|220.83|
|7|103|205|79|2019-04-11 11:15:00|94.86|
|8|101|246|77|2019-03-11 04:12:00|86.15|
|9|101|218|79|2019-03-11 08:59:00|75.52|
|10|103|211|77|2019-03-11 00:22:00|15.85|
|11|102|223|79|2019-03-11 10:44:00|59.69|
|12|104|211|77|2019-03-11 01:37:00|153.61|
|13|100|204|71|2019-03-11 07:00:00|190.29|
|14|100|231|79|2019-03-11 03:12:00|115.45|
|15|104|246|75|2019-04-11 08:52:00|225.91|
|16|102|231|77|2019-03-11 08:26:00|158.68|
|17|102|246|79|2019-04-11 01:15:00|62.72|
|18|100|205|77|2019-03-11 03:10:00|125.65|
|19|104|204|77|2019-04-11 08:14:00|129.75|
|20|101|231|75|2019-04-11 10:49:00|105.07|

---

## RESPUESTA

```sql
SELECT
    COUNT(DISTINCT customer_id) AS total_clientes,
    AVG(amount) AS cantidad_promedio
FROM postmates_orders;
```

---

## EXPLICACION

Cada fila representa una orden, asi que todos los `customer_id` presentes en la tabla corresponden a clientes que compraron al menos una vez.

Por eso se usa `COUNT(DISTINCT customer_id)` para contar clientes unicos y `AVG(amount)` para calcular el promedio del monto de las ordenes registradas.
