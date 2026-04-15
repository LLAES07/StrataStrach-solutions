# User with Most Approved Flags

**[ENG]**


Which user flagged the most distinct videos that ended up approved by YouTube? Output, in one column, their full name or names in case of a tie. In the user's full name, include a space between the first and the last name.


**[ESP]**

Cuales usuarios flagearon la mayor cantidad de videos que terminaron en un aprobado por youtube? Muestra en una columna ya sea el nombre completo o en el caso de empate el nombre. En el nombre completo del usuario incluye un espacio entre el primer y el último nombre.





# TABLA
### user_flags
| user_firstname | user_lastname | video_id    | flag_id |
| -------------- | ------------- | ----------- | ------- |
| Richard        | Hasson        | y6120QOlsfU | 0cazx3  |
| Mark           | May           | Ct6BUPvE2sM | 1cn76u  |
| Gina           | Korman        | dQw4w9WgXcQ | 1i43zk  |
| Mark           | May           | Ct6BUPvE2sM | 1n0vef  |
| Mark           | May           | jNQXAC9IVRw | 1sv6ib  |
| Gina           | Korman        | dQw4w9WgXcQ | 20xekb  |
| Mark           | May           | 5qap5aO4i9A | 4cvwuv  |
| Daniel         | Bell          | 5qap5aO4i9A | 4sd6dv  |
| Richard        | Hasson        | y6120QOlsfU | 6jjkvn  |
| Pauline        | Wilks         | jNQXAC9IVRw | 7ks264  |


### flag_review


|flag_id|reviewed_by_yt|reviewed_date|reviewed_outcome|
|---|---|---|---|
|0cazx3|FALSE|||
|1cn76u|TRUE|2022-03-15|REMOVED|
|1i43zk|TRUE|2022-03-15|REMOVED|
|1n0vef|TRUE|2022-03-15|REMOVED|
|1sv6ib|TRUE|2022-03-15|APPROVED|
|20xekb|TRUE|2022-03-17|REMOVED|
|4cvwuv|TRUE|2022-03-15|APPROVED|
|4l1tk7|FALSE|||
|4sd6dv|TRUE|2022-03-14|REMOVED|
|6jjkvn|TRUE|2022-03-16|APPROVED|
|7ks264|TRUE|2022-03-15|APPROVED|
|8946nx|FALSE|||
|8wwg0l|FALSE|||
|arydfd|TRUE|2022-03-15|APPROVED|
|bl40qw|TRUE|2022-03-16|REMOVED|

# RESPUESTA

```sql


WITH data AS (
        -- Concatena los nombres y cuenta la cantidad de videos
    SELECT
        CONCAT(user_firstname, ' ', user_lastname) AS nombre_completo,
        COUNT(DISTINCT u.video_id) AS total
    FROM user_flags u
    INNER JOIN flag_review f
        ON u.flag_id = f.flag_id
    WHERE
        f.reviewed_outcome ='APPROVED' AND
        f.reviewed_by_yt ='TRUE'
    GROUP BY
        CONCAT(user_firstname, ' ', user_lastname)
    ORDER BY 
        COUNT(DISTINCT u.video_id)  DESC

),

rk_ AS (
    -- Crea un ranking
    SELECT
        *,
        DENSE_RANK() OVER(ORDER BY total DESC) as rk
    FROM data
)

    -- Selecciona el ranking 1 para cada usuario
SELECT
    nombre_completo
FROM rk_
WHERE
    rk = 1;
    




```