# Total Shipment Weight

**[ENG]**

Calculate the total weight for each shipment and add it as a new column. Your output needs to have all the existing rows and columns in addition to the  new column that shows the total weight for each shipment. One shipment can have multiple rows.

**[ESP]**

Calcule el peso total para cada envío y agréguelo como una nueva columna. Tu consulta debe tener todas las filas y columnas existentes sumado a la nueva columna que mueste el peso total de cada envío. Un envío puede tener múltiples filas.



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