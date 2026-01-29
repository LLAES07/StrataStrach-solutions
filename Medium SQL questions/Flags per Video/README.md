For each video, find how many unique users flagged it. A unique user can be identified using the combination of their first name and last name. Do not consider rows in which there is no flag ID.
# Tabla

### user_flags


|user_firstname|user_lastname|video_id|flag_id|
|---|---|---|---|
|Richard|Hasson|y6120QOlsfU|0cazx3|
|Mark|May|Ct6BUPvE2sM|1cn76u|
|Gina|Korman|dQw4w9WgXcQ|1i43zk|
|Mark|May|Ct6BUPvE2sM|1n0vef|
|Mark|May|jNQXAC9IVRw|1sv6ib|
|Gina|Korman|dQw4w9WgXcQ|20xekb|
|Mark|May|5qap5aO4i9A|4cvwuv|
|Daniel|Bell|5qap5aO4i9A|4sd6dv|
|Richard|Hasson|y6120QOlsfU|6jjkvn|
|Pauline|Wilks|jNQXAC9IVRw|7ks264|
|Courtney||dQw4w9WgXcQ||
|Helen|Hearn|dQw4w9WgXcQ|8946nx|
|Mark|Johnson|y6120QOlsfU|8wwg0l|
|Richard|Hasson|dQw4w9WgXcQ|arydfd|
|Gina|Korman|||
|Mark|Johnson|y6120QOlsfU|bl40qw|



# RESPUESTA

```sql

SELECT
    video_id,
    COUNT(DISTINCT(CONCAT(COALESCE(user_firstname, ''), ' ', COALESCE(user_lastname, '')))) AS unique_user_count
FROM
    user_flags
WHERE
    flag_id IS NOT NULL
GROUP BY
    video_id;
```