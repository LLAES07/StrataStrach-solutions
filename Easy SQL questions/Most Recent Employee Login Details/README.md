# Most Recent Employee Login Details



**[ENG]**

Amazon's information technology department is looking for information on employees' most recent logins.


The output should include all information related to each employee's most recent login.


**[ESP]**

El departamento de infromación tecnologica de amazon esta buscando la informacion de los logins mas recientes de sus empleados.

Muestra todoa la información que sea del loging más reciente.

### TABLA

worker_logins


|id|worker_id|login_timestamp|ip_address|country|region|city|device_type|
|---|---|---|---|---|---|---|---|
|0|1|2021-12-14 09:01:00|65.111.191.14|USA|Florida|Miami|desktop|
|1|4|2021-12-18 10:05:00|46.212.154.172|Norway|Viken|Skjetten|desktop|
|2|3|2021-12-15 08:55:00|80.211.248.182|Poland|Mazovia|Warsaw|desktop|
|3|5|2021-12-19 09:55:00|10.2.135.23|France|North|Roubaix|desktop|
|4|6|2022-01-03 11:55:00|185.103.180.49|Spain|Catalonia|Alcarras|desktop|
|5|7|2022-01-01 07:55:00|212.102.111.33|Spain|Valencia|Sueca|desktop|
|6|8|2022-01-15 09:45:00|10.1.14.224|Italy|Lombardy|Borgarello|desktop|
|7|1|2022-01-15 09:55:00|65.111.191.14|USA|Florida|Miami|desktop|
|8|2|2022-01-05 10:55:00|66.68.93.191|USA|Texas|Austin|desktop|
|9|4|2021-12-23 09:59:00|46.212.154.172|Norway|Viken|Skjetten|mobile|
|10|5|2021-12-15 09:58:00|10.2.135.23|France|North|Roubaix|desktop|
|11|6|2022-01-14 10:45:00|185.103.180.49|Spain|Catalonia|Alcarras|mobile|
|12|7|2022-01-08 08:59:00|212.102.111.33|Spain|Valencia|Sueca|desktop|
|13|3|2022-01-06 08:46:00|80.211.248.182|Poland|Mazovia|Warsaw|desktop|
|14|2|2022-01-10 09:52:00|66.68.93.191|USA|Texas|Austin|desktop|
|15|4|2022-01-24 08:48:00|46.212.154.172|Norway|Viken|Skjetten|desktop|
|16|3|2022-01-25 08:58:00|80.211.248.182|Poland|Mazovia|Warsaw|desktop|
|17|6|2022-01-24 09:56:00|185.103.180.49|Spain|Catalonia|Alcarras|desktop|
|18|8|2022-01-25 09:59:00|10.1.14.224|Italy|Lombardy|Borgarello|desktop|
|19|7|2022-01-26 10:55:00|212.102.111.33|Spain|Valencia|Sueca|mobile|

# RESPUESTA


```sql

WITH ct1 as (
    select
        *,
        ROW_NUMBER() OVER(PARTITION BY worker_id ORDER BY login_timestamp DESC) AS rk
    from worker_logins 
)

SELECT
    id,
    worker_id,
    login_timestamp,
    ip_address,
    country	,
    region,
    city,	
    device_type
FROM ct1
WHERE rk = 1

```

# EXPLICACION

Primero se ordenan los registros por fecha de inicio de sesion para encontrar el acceso mas reciente de cada empleado. Luego se filtran o agrupan los datos para quedarnos con la ultima entrada por usuario.

De esa manera se obtiene el detalle de login mas actual y se conserva la informacion clave del evento, como el lugar y el tipo de dispositivo. La consulta termina mostrando una sola fila por empleado con su acceso mas reciente.
