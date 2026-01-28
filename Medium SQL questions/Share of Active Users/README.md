Calculate the percentage of users who are both from the US and have an 'open' status, as indicated in the fb_active_users table.

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