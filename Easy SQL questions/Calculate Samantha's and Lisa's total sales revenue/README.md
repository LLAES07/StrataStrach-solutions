# Calculate Samantha's and Lisa's total sales revenue




# 📌 PROBLEMA

**[ENG]**

What is the total sales revenue of Samantha and Lisa?



**[ESP]**

Cual es el total de ventas de Samantha y Lisa?






# TABLA



# 💻 REPSUESTA

```sql

SELECT
    salesperson,
    SUM(sales_revenue) AS total_revenue
FROM sales_performance
WHERE lower(salesperson) IN ('samantha', 'lisa')
GROUP BY
    salesperson


```

# 🧠 EXPLICACIÓN

Necesitamos el total de revenue para dos personas en especifico. Con esto en mente primero filtramos por los nombres solicitados usando `lower` para normalizar los nombres pasados. Posterior a esto agrupamos por el nombre que en nuestro caso solo estarán los de las personas filtradas. Por ultimo sumamos los revenue.