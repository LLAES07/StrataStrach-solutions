# Find non-HS SAT scores

---

**[ENG]**
Find SAT scores of students whose high school names do not end with 'HS'.

**[ESP]**

Encuentra los escores SAT de los estudiantes que tienen nombres de escuelas que no terminan en 'HS'.

### Table

sat_scores

| school        | teacher      | student_id | sat_writing | sat_verbal | sat_math | hrs_studied | id | average_sat | love |
| ------------- | ------------ | ---------- | ----------- | ---------- | -------- | ----------- | -- | ----------- | ---- |
| Washington HS | Frederickson | 1          | 583         | 307        | 528      | 190         | 1  | 583         |      |
| Washington HS | Frederickson | 2          | 401         | 791        | 248      | 149         | 2  | 401         |      |
| Washington HS | Frederickson | 3          | 523         | 445        | 756      | 166         | 3  | 523         |      |
| Washington HS | Frederickson | 4          | 306         | 269        | 327      | 137         | 4  | 306         |      |
| Washington HS | Frederickson | 5          | 300         | 539        | 743      | 115         | 5  | 300         |      |
| Washington HS | Frederickson | 6          | 213         | 500        | 771      | 173         | 6  | 213         |      |
| Washington HS | Frederickson | 7          | 548         | 683        | 740      | 47          | 7  | 548         |      |
| Washington HS | Frederickson | 8          | 314         | 503        | 341      | 174         | 8  | 314         |      |
| Washington HS | Frederickson | 9          | 401         | 630        | 666      | 111         | 9  | 401         |      |

---

# RESPUESTA

```sql
SELECT 
    * 
FROM sat_scores
WHERE 
    TRIM(school) NOT LIKE '%HS';
```

---

# 📊 Explicación

La pregunta nos pide las escuelas que no tengan el patron `HS` en el término del nombre de la escuela. Por lo tanto es una condición de filtro ya que imponemos una condición `NOT LIKE '%HS'`. Usamos `TRIM` para asegurarnos que no hay espacios principalmente a la derecha de la palabra para tener una coincidencia en caso que temrine en HS.
