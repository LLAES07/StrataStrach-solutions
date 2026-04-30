# Calculate Samantha's and Lisa's total sales revenue

# ðŸ“Œ PROBLEMA

**[ENG]**

What is the total sales revenue of Samantha and Lisa?

**[ESP]**

Cual es el total de ventas de Samantha y Lisa?

# TABLA

# ðŸ’» REPSUESTA

```sql
SELECT
    salesperson,
    SUM(sales_revenue) AS total_revenue
FROM sales_performance
WHERE lower(salesperson) IN ('samantha', 'lisa')
GROUP BY
    salesperson
```

# ðŸ§  EXPLICACIÃ“N

Necesitamos obtener el total de ventas de dos personas especificas, asi que el primer paso es filtrar la tabla para quedarnos solo con `Samantha` y `Lisa`. Para hacer ese filtro de forma mas segura se usa `LOWER(salesperson)`, lo que permite comparar los nombres aunque en la tabla aparezcan con una combinacion distinta de mayusculas y minusculas.

Despues se agrupa por `salesperson` porque el resultado esperado es un total por cada vendedora, no un solo acumulado general. Finalmente, `SUM(sales_revenue)` suma todos los ingresos de cada una y devuelve el revenue total correspondiente a Samantha y Lisa.
