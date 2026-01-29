The election is conducted in a city and everyone can vote for one or more candidates, or choose not to vote at all. Each person has 1 vote so if they vote for multiple candidates, their vote gets equally split across these candidates. For example, if a person votes for 2 candidates, these candidates receive an equivalent of 0.5 vote each. Some voters have chosen not to vote, which explains the blank entries in the dataset.


Find out who got the most votes and won the election. Output the name of the candidate or multiple names in case of a tie.
To avoid issues with a floating-point error you can round the number of votes received by a candidate to 3 decimal places.

# TABLA
### voting_results

| voter    | candidate |
| -------- | --------- |
| Kathy    |           |
| Charles  | Ryan      |
| Charles  | Christine |
| Charles  | Kathy     |
| Benjamin | Christine |
| Anthony  | Paul      |
| Anthony  | Anthony   |
| Edward   | Ryan      |
| Edward   | Paul      |
| Edward   | Kathy     |
| Terry    |           |
| Nancy    | Ryan      |
| Nancy    | Nicole    |
| Nancy    | Paul      |
| Nancy    | Christine |

# RESPUESTA

```sql
WITH votos AS (
    SELECT
        voter,
        1.0/COUNT(*) AS ratio_votos
    FROM voting_results
    WHERE
        candidate IS NOT NULL
    GROUP BY
        voter
    
)


SELECT
    candidate
FROM voting_results v
INNER JOIN votos v2
    ON v.voter = v2.voter
WHERE 
    candidate IS NOT NULL
GROUP BY
    candidate
ORDER BY
    ROUND(SUM(ratio_votos), 3) DESC
LIMIT 1;

```