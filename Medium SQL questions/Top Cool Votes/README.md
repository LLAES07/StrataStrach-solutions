Find the review_text that received the highest number of  cool votes.
Output the business name along with the review text with the highest number of cool votes.

# Tabla

### yelp_reviews


| business_name        | review_id              | user_id                | stars | review_date | review_text                                                                                                                                            | funny | useful | cool |
| -------------------- | ---------------------- | ---------------------- | ----- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ------ | ---- |
| AutohausAZ           | C4TSIEcazRay0qIRPeMAFg | jlbPUcCRiXlMtarzi9sW5w | 5     | 2011-06-27  | Autohaus is my main source for parts for an old Mercedes that has been in the family since new that I am restoring. The old beater is truly a labor of | 1     | 2      | 1    |
| Citizen Public House | ZZ0paqUsSX-VJbfodTp1cQ | EeCWSGwMAPzwe_c1Aumd1w | 4     | 2013-03-18  | First time in PHX. Friend recommended. Friendly waitstaff. They were understaffed and extremely busy, but we never knew. The short ribs were tende     | 0     | 0      | 0    |

# RESPUESTA
```sql

SELECT
    business_name, 
    review_text
FROM yelp_reviews
WHERE 
    cool = ( -- Cantidad maxima de cool
            SELECT 
                MAX(cool) 
            FROM yelp_reviews
            );


```