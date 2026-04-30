# Sales Revenue

**[ENG]**

Calculate the sales revenue for the year 2021.

**[ESP]**

Calcula el total de ventas para el ano 2021

### Tabla

amazon_sales

| order_id | order_date | order_total |
| -------- | ---------- | ----------- |
| O1001    | 2020-10-08 | 30          |
| O1002    | 2020-11-05 | 50          |
| O1003    | 2020-11-12 | 100         |
| O1004    | 2020-12-16 | 300         |
| O1005    | 2021-01-01 | 50          |
| O1006    | 2021-02-04 | 60          |
| O1008    | 2021-02-13 | 60          |
| O1007    | 2021-02-25 | 80          |
| O1009    | 2021-03-06 | 40          |
| O1010    | 2021-04-02 | 80          |

# RESPUESTA

```sql
SELECT
    SUM(order_total) AS revenue_2021
FROM amazon_sales
WHERE
    EXTRACT(YEAR FROM order_date)= '2021'
```

# EXPLICACION

Para resolverlo solo hace falta sumar el valor de los pedidos que pertenecen al ano 2021. El filtro `EXTRACT(YEAR FROM order_date) = '2021'` deja fuera cualquier orden de 2020 u otros anos, de manera que la suma trabaje unicamente con el periodo solicitado.

Una vez filtradas esas filas, `SUM(order_total)` acumula el importe de cada pedido y devuelve un solo resultado llamado `revenue_2021`. No se necesita `GROUP BY` porque el ejercicio pide el total general del ano, no un desglose por mes o por cliente.
