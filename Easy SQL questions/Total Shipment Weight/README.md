# Total Shipment Weight

**[ENG]**

Calculate the total weight for each shipment and add it as a new column. Your output needs to have all the existing rows and columns in addition to the new column that shows the total weight for each shipment. One shipment can have multiple rows.

**[ESP]**

Calcule el peso total para cada envio y agreguelo como una nueva columna. Tu consulta debe tener todas las filas y columnas existentes sumado a la nueva columna que muestre el peso total de cada envio. Un envio puede tener multiples filas.

### TABLA

amazon_shipment

|shipment_id|sub_id|weight|shipment_date|
|---|---|---|---|
|101|1|10|2021-08-30|
|101|2|20|2021-09-01|
|101|3|10|2021-09-05|
|102|1|50|2021-09-02|
|103|1|25|2021-09-01|
|103|2|30|2021-09-02|
|104|1|30|2021-08-25|
|104|2|10|2021-08-26|
|105|1|20|2021-09-02|

### RESPUESTA

```sql
SELECT
    *,
    SUM(weight) OVER(PARTITION BY shipment_id) AS total_weights
FROM amazon_shipment;
```

# EXPLICACION

Aqui no basta con agrupar y devolver un solo registro por envio, porque el resultado debe conservar todas las filas originales. Por eso se usa una funcion de ventana: `SUM(weight) OVER (PARTITION BY shipment_id)` suma el peso de todas las filas que pertenecen al mismo `shipment_id`, pero mantiene cada registro individual en la salida.

El efecto practico es que cada fila sigue mostrando su `sub_id`, `weight` y `shipment_date`, y ademas recibe una columna nueva con el peso total del envio completo. Esa es justamente la ventaja de usar una ventana en lugar de un `GROUP BY`.
