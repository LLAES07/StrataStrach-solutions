# Pending Claims


Count how many claims submitted in December 2021 are still pending. A claim is pending when it has neither an acceptance nor rejection date.

### Tabla
| laim_id | account_id | date_submitted | date_accepted | date_rejected |
| ------- | ---------- | -------------- | ------------- | ------------- |
| 3075    | A41        | 2022-01-05     |               |               |
| 3065    | A41        | 2021-12-01     |               |               |
| 3061    | A41        | 2020-12-15     |               |               |
| 3074    | A42        | 2022-01-03     | 2022-01-14    |               |
| 3069    | A42        | 2021-12-19     |               | 2021-12-23    |
| 3063    | A43        | 2021-11-23     | 2021-11-24    |               |
| 3076    | A44        | 2022-01-15     |               | 2022-01-17    |
| 3070    | A44        | 2021-12-22     |               |               |
| 3073    | A45        | 2021-12-31     |               |               |
| 3072    | A45        | 2021-12-28     | 2021-12-29    | 2022-01-10    |
| 3071    | A46        | 2021-12-28     |               |               |
| 3062    | A46        | 2021-11-07     |               |               |
| 3066    | A47        | 2021-12-14     | 2021-12-28    |               |
| 3064    | A47        | 2021-11-28     |               | 2021-12-13    |
| 3067    | A48        | 2021-12-14     |               |               |
| 3068    | A52        | 2021-12-16     |               | 2022-01-02    |


# RESPUESTA

```sql

SELECT
    COUNT(claim_id) AS pending_claims
FROM cvs_claims
WHERE 
    date_submitted >= '2021-12-01' AND
    date_submitted <= '2021-12-31' AND
    date_accepted IS NULL AND
    date_rejected IS NULL
```