# Rank guests based on their ages

## 📌 PROBLEMA

**[ENG]**
Rank guests based on their ages.
Output the guest id along with the corresponding rank.
Order records by the age in descending order.

**[ESP]**
Crea un ranking de los huespedes segun sus edades.
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

# 💻 RESPUESTA

```sql
SELECT 
    guest_id,
    ROW_NUMBER() OVER (ORDER BY age DESC) AS rank
FROM airbnb_guests
ORDER BY age DESC;
```

# 📊 Explicación

Para construir el ranking se usa `ROW_NUMBER()`, una funcion de ventana que asigna un numero consecutivo a cada fila segun el orden definido dentro de `OVER (...)`. Como el enunciado pide ordenar por edad de mayor a menor, el criterio utilizado es `ORDER BY age DESC`.

El resultado es que el huesped con mayor edad recibe el rango `1`, el siguiente recibe `2`, y asi sucesivamente. Luego se repite ese mismo orden en la consulta principal para que las filas salgan mostradas exactamente en el mismo orden del ranking generado.
