# Active Users Per Platform

## 📌 PROBLEMA

**[ENG]**

For each platform (e.g. Windows, iPhone, iPad etc.), calculate the number of users. Count the number of distinct users per platform, regardless of whether they used other platforms. Output the name of the platform with the corresponding number of users.


**[ESP]**

Para cada plataforma (e.g. Windows, iPhone, iPad etc.), calcula el número de usuarios. Cuenta el numero de usuarios distintos por plataforma, ya sea que usen otras plataformas. Muestra el nombre de la plataforma con el numero correspondiente de usuarios


### Tabla

user_sessions


|session_id|user_id|session_starttime|session_endtime|platform|
|---|---|---|---|---|
|1|U1|2020-01-01 12:14:28|2020-01-01 12:16:08|Windows|
|2|U1|2020-01-01 18:23:50|2020-01-01 18:24:00|Windows|
|3|U1|2020-01-01 08:15:00|2020-01-01 08:20:00|IPhone|
|4|U2|2020-01-01 10:53:10|2020-01-01 10:53:30|IPhone|
|5|U2|2020-01-01 18:25:14|2020-01-01 18:27:53|IPhone|
|6|U2|2020-01-01 11:28:13|2020-01-01 11:31:33|Windows|
|7|U3|2020-01-01 06:46:20|2020-01-01 06:58:13|Android|
|8|U3|2020-01-01 10:53:10|2020-01-01 10:53:50|Android|
|9|U3|2020-01-01 13:13:13|2020-01-01 13:34:34|Windows|
|10|U4|2020-01-01 08:12:00|2020-01-01 12:23:11|Windows|
|11|U4|2020-01-01 21:54:03|2020-01-01 21:54:04|IPad|

# 💻 RESPUESTA



```sql

SELECT 
    -- Muestra la plataforma y los usuarios unicos por plataforma
    platform, 
    COUNT(DISTINCT user_id) AS total_users
FROM user_sessions
-- Agrupa por plataforma
GROUP BY platform;

```