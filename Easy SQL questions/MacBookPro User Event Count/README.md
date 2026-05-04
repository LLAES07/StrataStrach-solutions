
# MacBookPro User Event Count

**[ENG]**

Count the number of user events performed by MacBookPro users.Output the result along with the event name. Sort the result based on the event count in the descending order.

**[ES]**

Cuenta el número de eventos de usuario realizados por los usuarios de MacBookPro. Muestra el resultado junto con el nombre del evento. Ordena el resultado en orden descendiente.


## tabla
| user_id | occurred_at         | event_type  | event_name   | location      | device                 |
| ------- | ------------------- | ----------- | ------------ | ------------- | ---------------------- |
| 6991    | 2014-06-09 18:26:54 | engagement  | home_page    | United States | iphone 5               |
| 18851   | 2014-08-29 13:18:38 | signup_flow | enter_info   | Russia        | asus chromebook        |
| 14998   | 2014-07-01 12:47:56 | engagement  | login        | France        | hp pavilion desktop    |
| 8186    | 2014-05-23 10:44:16 | engagement  | home_page    | Italy         | macbook pro            |
| 9626    | 2014-07-31 17:15:14 | engagement  | login        | Russia        | nexus 7                |
| 16460   | 2014-07-24 18:43:19 | signup_flow | create_user  | United States | samsung galaxy note    |
| 10101   | 2014-08-27 05:54:28 | engagement  | home_page    | Singapore     | dell inspiron notebook |
| 2670    | 2014-05-10 10:03:34 | engagement  | like_message | United States | nexus 7                |

# Respuesta

```sql

SELECT
    event_name,
    COUNT(event_name) AS event_count
FROM playbook_events
WHERE 
    LOWER(device) ~ '^macbook\s?pro'
GROUP BY 
    event_name
ORDER BY 
    event_count DESC;

```

# 📊 Explicación

Para contar los eventos realizados específicamente por usuarios de MacBook Pro, primero aplicamos un filtro en la cláusula `WHERE` usando una expresión regular (`~ '^macbook\s?pro'`) sobre la columna `device` (convertida a minúsculas con `LOWER`). Luego, agrupamos los resultados por `event_name` y usamos `COUNT(*)` para obtener el total de ocurrencias por cada tipo de evento, ordenando finalmente de forma descendente.

