Find the top 10 ranked songs in 2010. Output the rank, group name, and song name, but do not show the same song twice. Sort the result based on the rank in ascending order.

## billboard_top_100_year_end

| year | year_rank | group_name    | artist        | song_name                                | id  |
| ---- | --------- | ------------- | ------------- | ---------------------------------------- | --- |
| 1956 | 1         | Elvis Presley | Elvis Presley | Heartbreak Hotel                         | 1   |
| 1956 | 2         | Elvis Presley | Elvis Presley | Don't Be Cruel                           | 2   |
| 1956 | 3         | Nelson Riddle | Nelson Riddle | Lisbon Antigua                           | 3   |
| 1956 | 4         | Platters      | Platters      | My Prayer                                | 4   |
| 1956 | 5         | Gogi Grant    | Gogi Grant    | The Wayward Wind                         | 5   |
| 1956 | 6         | Les Baxter    | Les Baxter    | The Poor People Of Paris                 | 6   |
| 1956 | 7         | Doris Day     | Doris Day     | Whatever Will Be Will Be (Que Sera Sera) | 7   |


# RESPUESTA

 ```sql
 
 SELECT
    DISTINCT song_name,
    year_rank,
    group_name
FROM billboard_top_100_year_end
WHERE 
    year = 2010 
ORDER BY 
    year_rank ASC
LIMIT 10

 ```