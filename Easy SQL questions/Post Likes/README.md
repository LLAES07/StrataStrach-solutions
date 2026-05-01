# Post Likes

**[ENG]**

You are given a list of posts of a Facebook user. Find the average number of likes.

**[ESP]**

Tienes una lista de publicaciones de un usuario de Facebook. Encuentra el numero promedio de likes.

### TABLA

| post_id | post_date  | no_of_likes |
| ------- | ---------- | ----------- |
| P001    | 2002-06-01 | 20          |
| P002    | 2002-06-02 | 1           |
| P003    | 2002-06-03 | 55          |
| P004    | 2002-06-04 | 21          |
| P005    | 2002-06-05 | 62          |
| P006    | 2002-06-06 | 36          |
| P007    | 2002-06-07 | 45          |
| P008    | 2002-06-08 | 33          |
| P009    | 2002-06-09 | 50          |
| P010    | 2002-06-10 | 104         |
| P011    | 2002-06-11 | 60          |
| P012    | 2002-06-12 | 56          |
| P013    | 2002-06-13 | 61          |
| P014    | 2002-06-14 | 12          |
| P015    | 2002-06-15 | 0           |
| P016    | 2002-06-16 | 22          |
| P017    | 2002-06-17 | 10          |
| P018    | 2002-06-18 | 66          |
| P019    | 2002-06-19 | 49          |
| P020    | 2002-06-20 | 60          |

# RESPUESTA

```sql
SELECT
    AVG(no_of_likes) as promedio_likes
FROM fb_posts
```

# EXPLICACION

Como el enunciado pide el promedio global de likes, no hace falta agrupar por publicacion, fecha ni por ningun otro campo. La consulta toma directamente todos los valores de `no_of_likes` presentes en la tabla y calcula su media aritmetica.

La funcion `AVG(no_of_likes)` se encarga de sumar internamente todos los likes y dividirlos por la cantidad de filas disponibles. El resultado final aparece en una sola columna llamada `promedio_likes`, que representa el promedio general de interacciones por post.
