# Latest Login Date


**[ENG]**
For each video game player, find the latest date when they logged in.

**[ESP]**

Para cada jugador de video juegos, encuentra la ultima fecha que logearon.


### TABLA

players_logins



|player_id|login_date|
|---|---|
|101|2021-12-14|
|101|2021-12-18|
|101|2021-12-15|
|101|2021-12-19|
|102|2021-12-31|
|102|2022-01-01|
|102|2022-01-15|
|102|2022-01-15|
|103|2020-12-22|
|103|2021-12-23|
|103|2021-12-15|
|104|2022-01-14|
|105|2022-01-08|
|105|2022-01-06|
|105|2022-01-10|
|106|2022-01-24|
|106|2022-01-25|
|106|2022-01-24|
|106|2022-01-25|
|106|2022-01-26|
|106|2022-01-26|


### RESPUESTA

```sql

SELECT
    player_id,
    MAX(login_date) AS fecha_ultimo_log

FROM players_logins
GROUP BY player_id

```

# EXPLICACION

Primero se revisan las fechas de login de cada usuario para ubicar la mas reciente. Luego se usa un maximo o un ordenamiento descendente para conservar solo la ultima fecha por usuario. El resultado muestra el acceso mas nuevo de cada cuenta.
