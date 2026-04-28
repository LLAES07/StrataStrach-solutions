# Users Activity Per Month Day

**[ENG]**

Return the total number of posts for each month, aggregated across all the years (i.e., posts in January 2019 and January 2020 are both combined into January). Output the month number (i.e., 1 for January, 2 for February) and the total number of posts in that month

**[ESP]**

Retorna el numero total de post por cada mes, agregado a travéz de los años (por ejemplo, los post de enero de 2019 y enero de 2020 se combinan en enero). Muestra el mes en formato numero y el total de numero de post de ese mes.

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

Primero se extrae el numero de mes desde `post_date` con `EXTRACT(MONTH FROM post_date)`. Luego se agrupa por ese mismo valor para juntar los posts de un mismo mes aunque pertenezcan a distintos anios, y finalmente `COUNT(post_id)` calcula el total de publicaciones para cada mes.
