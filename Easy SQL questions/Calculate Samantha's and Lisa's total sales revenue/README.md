# Calculate Samantha's and Lisa's total sales revenue

## 📌 PROBLEMA

**[ENG]**
What is the total sales revenue of Samantha and Lisa?

**[ESP]**
Cual es el total de ventas de Samantha y Lisa?

# TABLA

# 💻 RESPUESTA

```sql
SELECT
    salesperson,
    SUM(sales_revenue) AS total_revenue
FROM sales_performance
WHERE LOWER(salesperson) IN ('samantha', 'lisa')
GROUP BY salesperson;
```

# 📊 Explicación

La consulta primero filtra la tabla para quedarse solo con las filas de `Samantha` y `Lisa`. Para hacer ese filtro de forma mas segura se usa `LOWER(salesperson)`, de modo que la comparacion funcione aunque cambien las mayusculas o minusculas.

Despues se agrupa por `salesperson` porque el resultado esperado es un total por cada vendedora. Finalmente, `SUM(sales_revenue)` acumula el revenue de cada una y devuelve el total de ventas correspondiente.
