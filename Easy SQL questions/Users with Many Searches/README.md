# Users with Many Searches

# Paid Users In April 2020


**[ENG]**
Count the number of users who made more than 5 searches in August 2021.



**[ESP]**


### TABLA

| date       | search_id | user_id | age_group | search_query       |
| ---------- | --------- | ------- | --------- | ------------------ |
| 2021-04-02 | 126       | 516     | <30       | Economic Disease   |
| 2021-04-03 | 127       | 517     | 30-50     | Magnificent Zebra  |
| 2020-04-08 | 128       | 516     | <30       | Future Holiday     |
| 2021-04-12 | 129       | 519     | <30       | Enormous Crook     |
| 2021-04-17 | 151       | 518     | <30       | Imperfect Plough   |
| 2021-04-18 | 130       | 517     | 30-50     | Hapless Grape      |
| 2020-04-19 | 131       | 520     | 30-50     | Decorous Education |
| 2021-04-24 | 132       | 517     | 30-50     | Abusive Shade      |
| 2021-04-27 | 101       | 516     | <30       | Daily Motion       |
| 2021-04-27 | 152       | 518     | <30       | Curvy Bag          |
| 2021-04-30 | 102       | 521     | 50+       | Deserve Snow       |
| 2021-05-03 | 103       | 516     | <30       | Golf Product       |
| 2021-05-03 | 153       | 519     | <30       | Helium Initial     |
| 2021-05-04 | 154       | 517     | 30-50     | Under Tape         |
| 2021-05-05 | 155       | 516     | <30       | Zipper Darwin      |
| 2021-05-07 | 104       | 516     | <30       | Turtle Oberon      |
| 2021-05-08 | 105       | 518     | <30       | Plume Phantom      |
| 2020-05-09 | 156       | 517     | 30-50     | Pastel Noise       |
| 2021-05-10 | 106       | 520     | 30-50     | Alpha Canvas       |
| 2021-05-18 | 157       | 519     | <30       | Perform Belgium    |
| 2021-05-20 | 158       | 516     | <30       | Apropos Legal      |
| 2021-05-21 | 133       | 517     | 30-50     | Step Suggestion    |
| 2021-05-25 | 107       | 516     | <30       | Stamp Spot         |
| 2021-05-25 | 159       | 517     | 30-50     | Comfort Cracker    |
| 2020-05-30 | 108       | 516     | <30       | Color Crayon       |
| 2021-05-30 | 134       | 518     | <30       | Soap Stamp         |
| 2021-05-31 | 160       | 516     | <30       | Form Finger        |
| 2021-06-01 | 109       | 517     | 30-50     | Pail Plant         |
| 2021-06-04 | 110       | 516     | <30       | Bite Balance       |
| 2021-06-04 | 161       | 521     | 50+       | Berry Basin        |

# RESPUESTA


```sql

SELECT
    user_id
    
FROM fb_searches
WHERE date >= '2021-08-01' AND
      date <= '2021-08-31'
GROUP BY  user_id
HAVING COUNT(*)> 5

```