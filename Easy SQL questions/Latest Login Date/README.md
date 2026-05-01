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

Como el objetivo es encontrar la fecha mas reciente de login para cada jugador, la consulta agrupa primero por `player_id`. De esa forma cada grupo contiene todas las fechas registradas para un mismo usuario y puede resumirse en una sola fila.

Dentro de cada grupo, `MAX(login_date)` selecciona la fecha mayor, que coincide con el ultimo acceso cronologico. Este enfoque tambien maneja sin problema los duplicados, ya que aunque un jugador tenga varias filas con la misma fecha final, el maximo sigue siendo ese ultimo dia.

## EXPLICACION ADICIONAL

El `GROUP BY player_id` arma un grupo por jugador y permite que `MAX(login_date)` encuentre la fecha mayor dentro de cada conjunto. Eso evita revisar manualmente cada fila y resume la informacion en una sola salida por usuario. Asi la respuesta final conserva exactamente el ultimo acceso registrado para cada jugador.
