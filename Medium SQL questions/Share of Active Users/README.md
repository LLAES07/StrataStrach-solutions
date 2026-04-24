
# Share of Active Users

**[ENG]**

Calculate the percentage of users who are both from the US and have an 'open' status, as indicated in the fb_active_users table.

**[ESP]**

Calcula el porcentaje de usuarios que son de US y tienen status 'open', como indicado en la tabla fb_active_users.



# Tabla

### fb_active_users

| user_id | name             | status | country    |
| ------- | ---------------- | ------ | ---------- |
| 33      | Amanda Leon      | open   | Australia  |
| 27      | Jessica Farrell  | open   | Luxembourg |
| 18      | Wanda Ramirez    | open   | USA        |
| 50      | Samuel Miller    | closed | Brazil     |
| 16      | Jacob York       | open   | Australia  |
| 25      | Natasha Bradford | closed | USA        |
| 34      | Donald Ross      | closed | China      |
| 52      | Michelle Jimenez | open   | USA        |
| 11      | Theresa John     | open   | China      |


# RESPUESTA

```SQL


SELECT
    COUNT(*)*100.0/ (SELECT COUNT(*)
                    FROM fb_active_users    ) AS porcentaje

FROM fb_active_users
WHERE
    country = 'USA' AND status ='open'

```

# EXPLICACION

Primero se identifica a los usuarios activos segun la condicion del problema y luego se comparan con el total de usuarios disponibles. Despues se calcula la proporción que representan dentro del conjunto para obtener su participacion. Asi la salida refleja la cuota de usuarios activos sobre el total.
