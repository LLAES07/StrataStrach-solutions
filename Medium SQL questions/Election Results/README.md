
# Election Results

**[ENG]**

The election is conducted in a city and everyone can vote for one or more candidates, or choose not to vote at all. Each person has 1 vote so if they vote for multiple candidates, their vote gets equally split across these candidates. For example, if a person votes for 2 candidates, these candidates receive an equivalent of 0.5 vote each. Some voters have chosen not to vote, which explains the blank entries in the dataset.


Find out who got the most votes and won the election. Output the name of the candidate or multiple names in case of a tie.
To avoid issues with a floating-point error you can round the number of votes received by a candidate to 3 decimal places.

**[ESP]**

La elección se lleva a cabo en una ciudad y cada persona puede votar por uno o más candidatos, o optar por no votar. Cada persona tiene un voto por lo que si votan por multiples candidatos, su voto se ve repartido entre estos candidatos. Por ejemplo, si una persona vota por dos candidatos, estos reciven el equivalente a un voto de 0.5 cada uno. Algunos votantes han escogido no votar, lo que explica las entradas en blanco del dataset.

Encuentra quien obtuvo mas votos y ganó la elección. Muestra el nombre del candidato o varios nombres en caso de empate. Para evitar el problema del error por floating-point puedes redondear los votos recibidos por el candidato a 3 decimales.


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
    -- Genera un join entre voting_results y votos para que al lado de cada votante salga su ponderación por voto segun cuanto voto
FROM voting_results v
INNER JOIN votos v2
    ON v.voter = v2.voter
WHERE 
    candidate IS NOT NULL
GROUP BY
    candidate
ORDER BY
    -- Suma la cantidad de votos y los ordena de mayor a menor
    ROUND(SUM(ratio_votos), 3) DESC
LIMIT 1;

```