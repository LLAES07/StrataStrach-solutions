Identify the IDs of students who scored exactly at the median for the SAT writing section.

# TABLA

### sat_scores


| school        | teacher      | student_id | sat_writing | sat_verbal | sat_math | hrs_studied | id  | average_sat | love |
| ------------- | ------------ | ---------- | ----------- | ---------- | -------- | ----------- | --- | ----------- | ---- |
| Washington HS | Frederickson | 1          | 583         | 307        | 528      | 190         | 1   | 583         |      |
| Washington HS | Frederickson | 2          | 401         | 791        | 248      | 149         | 2   | 401         |      |
| Washington HS | Frederickson | 3          | 523         | 445        | 756      | 166         | 3   | 523         |      |
| Washington HS | Frederickson | 4          | 306         | 269        | 327      | 137         | 4   | 306         |      |
| Washington HS | Frederickson | 5          | 300         | 539        | 743      | 115         | 5   | 300         |      |
| Washington HS | Frederickson | 6          | 213         | 500        | 771      | 173         | 6   | 213         |      |
| Washington HS | Frederickson | 7          | 548         | 683        | 740      | 47          | 7   | 548         |      |
| Washington HS | Frederickson | 8          | 314         | 503        | 341      | 174         | 8   | 314         |      |
| Washington HS | Frederickson | 9          | 401         | 630        | 666      | 111         | 9   | 401         |      |
| Washington HS | Frederickson | 10         | 532         | 683        | 316      | 134         | 10  | 532         |      |


# RESPUESTA

```sql
SELECT 
    sat_writing
FROM sat_scores
ORDER BY sat_writing
LIMIT 2 OFFSET (SELECT FLOOR((COUNT(*) - 1) / 2) FROM sat_scores)
```