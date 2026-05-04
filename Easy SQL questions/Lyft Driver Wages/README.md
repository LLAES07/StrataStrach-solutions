# Lyft Driver Wages

**[ENG]**

Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD. Output all details related to retrieved records.

**[ES]**

Encuentra los conductores de Lyft que ganan ya sea igual o menor que 30k USD o igual o mayor que 70k USD. Muestra todos los detalles relacionados con los registros recuperados.

# TABLA

### Table

lyft_drivers

|index|start_date|end_date|yearly_salary|
|---|---|---|---|
|0|2018-04-02||48303|
|1|2018-05-30||67973|
|2|2015-04-05||56685|
|3|2015-01-08||51320|
|4|2017-03-09||67507|
|5|2015-09-07||55155|
|6|2016-05-22|2018-08-06|35847|
|7|2015-09-29|2018-07-20|46974|
|8|2015-09-15|2019-04-30|54316|

# RESPUESTA

```sql
SELECT
    *
FROM lyft_drivers
WHERE
    yearly_salary <= 30000 OR 
    yearly_salary > 70000;
```

# 📊 Explicación

La consulta filtra a los conductores de Lyft basándose en sus ingresos anuales (`yearly_salary`). Utilizamos la cláusula `WHERE` para encontrar a aquellos que ganan 30,000 USD o menos, **o** 70,000 USD o más. El operador `OR` nos permite capturar ambos extremos de la escala salarial solicitada en una sola lista de resultados.

El enunciado pide recuperar todos los registros cuyo yearly_salary este fuera del rango intermedio. Por eso el WHERE usa dos condiciones unidas con OR: una para salarios menores o iguales a 30000 y otra para salarios mayores a 70000.

Como la salida debe mostrar todos los detalles del conductor, se utiliza SELECT * en lugar de elegir columnas puntuales. Asi la consulta devuelve exactamente los registros extremos de salario junto con toda su informacion disponible.
