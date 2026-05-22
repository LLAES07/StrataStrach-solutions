# Products Report Summary

## PROBLEMA

**[ENG]**
Find the number of unique transactions and total sales for each of the product categories in 2017. Output the product categories, number of transactions, and total sales in descending order. The `sales` column represents the total cost the customer paid for the product, so no additional calculations need to be done on the column. Only include product categories that have products sold.

**[ESP]**
Encuentra la cantidad de transacciones unicas y las ventas totales para cada categoria de producto en 2017. Muestra la categoria, el numero de transacciones y el total de ventas en orden descendente. La columna `sales` ya representa el costo total pagado por el cliente, por lo que no se necesitan calculos extra. Incluye solo categorias con productos vendidos.

---

### TABLA

`wfm_transactions`

`wfm_products`

Tablas de ejemplo omitidas por extension.

---

## RESPUESTA

```sql
SELECT
    p.product_category,
    COUNT(DISTINCT t.transaction_id) AS num_transactions,
    SUM(t.sales) AS total_sales
FROM wfm_transactions t
JOIN wfm_products p
    ON t.product_id = p.product_id
WHERE EXTRACT(YEAR FROM t.transaction_date) = 2017
GROUP BY p.product_category
ORDER BY total_sales DESC;
```

---

## EXPLICACION

Primero se unen `wfm_transactions` y `wfm_products` para relacionar cada venta con su categoria de producto.

Luego se filtran solo las transacciones de 2017, se agrupa por `product_category` y se calculan dos metricas: el numero de transacciones unicas con `COUNT(DISTINCT transaction_id)` y el total de ventas con `SUM(sales)`. Al final se ordena por `total_sales` de mayor a menor.
