# Rank guests based on their ages




## 📌 PROBLEMA

**[ENG]**
Rank guests based on their ages.
Output the guest id along with the corresponding rank.
Order records by the age in descending order.

**[ESP]**

Crea un ranking de los huespedes según sus edades.
Muestra el id con su correspondiente ranking.
Ordena los registros por la edad en orden descendente.


# TABLA

airbnb_guests

|guest_id|nationality|gender|age|
|---|---|---|---|
|0|Mali|M|21|
|1|China|F|23|
|2|Mali|F|27|
|3|Australia|F|24|
|4|Luxembourg|M|19|
|5|USA|F|33|
|6|Brazil|M|32|
|7|China|M|27|
|8|Australia|M|37|
|9|USA|M|29|
|10|Luxembourg|F|28|
|11|Brazil|F|24|

#  💻 REPSUESTA

```sql

SELECT 
    guest_id,
    ROW_NUMBER() OVER (ORDER BY age DESC) AS rank
FROM airbnb_guests
ORDER BY age DESC;
```

# 🧠 EXPLICACIÓN

Necesitamos un raking de edad y como no nos dan restricciones voy a usar `ROW_NUMBER()` puesto que me gener aun ranking contando las filas (asumiendo que no hay duplicados). Con este ranking listo ordenamos por `age` en orden descendente.