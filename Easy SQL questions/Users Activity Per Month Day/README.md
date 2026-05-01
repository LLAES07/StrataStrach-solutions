# Users Activity Per Month Day

**[ENG]**

Return the total number of posts for each month, aggregated across all the years (i.e., posts in January 2019 and January 2020 are both combined into January). Output the month number (i.e., 1 for January, 2 for February) and the total number of posts in that month

**[ESP]**

Retorna el numero total de post por cada mes, agregado a traves de los anos (por ejemplo, los post de enero de 2019 y enero de 2020 se combinan en enero). Muestra el mes en formato numero y el total de numero de post de ese mes.

### TABLA

facebook_posts

|ost_id|poster|post_text|post_keywords|post_date|
|---|---|---|---|---|
|0|2|The Lakers game from last night was great.|[basketball,lakers,nba]|2019-01-01|
|1|1|Lebron James is top class.|[basketball,lebron_james,nba]|2019-01-02|
|2|2|Asparagus tastes OK.|[asparagus,food]|2019-01-01|
|3|1|Spaghetti is an Italian food.|[spaghetti,food]|2019-01-02|
|4|3|User 3 is not sharing interests|[#spam#]|2019-01-01|
|5|3|User 3 posts SPAM content a lot|[#spam#]|2019-01-02|

# RESPUESTA

```sql
select
    EXTRACT(MONTH FROM post_date) AS mes,
    COUNT(post_id)
FROM facebook_posts
GROUP BY EXTRACT(MONTH FROM post_date)
```

# EXPLICACION

El detalle importante del ejercicio es que no se debe separar por ano, sino combinar todos los registros que pertenezcan al mismo mes sin importar el periodo. Por eso se usa `EXTRACT(MONTH FROM post_date)`, que convierte cada fecha en su numero de mes y elimina el componente del ano para el agrupamiento.

Despues `GROUP BY` junta todas las publicaciones con el mismo valor de mes y `COUNT(post_id)` calcula cuantas filas hay en cada grupo. Asi enero de distintos anos se suma en un mismo bloque, febrero en otro, y asi sucesivamente.
