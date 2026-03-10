# Account Registrations

## 📌 PROBLEMA

**[ENG]**

Find the number of account registrations according to the signup date. Output the year months (YYYY-MM) and their corresponding number of registrations.


**[ESP]**

Encuentra el numero de cuentas registradas según la fecha de registro. Muestra el año en formato yyyy-mm y su correpsondiente numero de registro.

### TABLA

#### noom_signups

|signup_id|started_at|plan_id|
|---|---|---|
|S001|2018-10-06|101|
|S002|2018-11-01|101|
|S003|2018-11-02|103|
|S004|2018-11-05|103|
|S005|2018-11-15|102|
|S006|2018-12-14|102|
|S007|2019-01-01|101|
|S008|2019-01-14|102|
|S009|2019-01-27|101|
|S010|2019-02-04|102|
|S011|2019-02-05|103|
|S012|2019-02-23|102|
|S013|2019-04-10|103|
|S014|2019-05-20|101|
|S015|2019-05-24|102|
|S016|2019-06-30|103|
|S017|2019-07-24|102|
|S018|2019-08-10|103|
|S019|2019-09-05|101|
|S020|2019-09-09|101|
|S021|2019-09-11|101|
|S022|2019-09-23|102|
|S023|2019-10-10|101|
|S024|2019-12-10|101|
|S025|2020-01-02|101|


# 💻 RESPUESTA

```sql
SELECT
    CONCAT(EXTRACT(YEAR FROM started_at), '-', EXTRACT(MONTH FROM started_at)) AS mes_año,
    COUNT(*) AS total
FROM noom_signups
GROUP BY 1 
ORDER BY 1;
```

# 📊 Explicación

Cada fila de la tabla corresponde a un registro correspondiente a un registro con su fecha y plan. Con esto en mente vemos que tenemos una fecha en formato yyyy-mm-dd por lo que necesitamos extraer tanto el año como el mes. Esto lo logramos utilizando extract en la columna `started_at`, envueltas en la funcion `CONCAT` para poder unir estas y ser la nueva columna por donde generar un group by y un order by. Con esto ya podemos contar los registros, otorgandonos lo solicitado