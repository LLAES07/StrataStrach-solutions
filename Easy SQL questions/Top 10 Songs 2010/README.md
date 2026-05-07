# Top 10 Songs 2010

## 📌 PROBLEMA

**[ENG]**
Find the top 10 ranked songs in 2010. Output the rank, group name, and song name, but do not show the same song twice. Sort the result based on the rank in ascending order.

**[ESP]**
Encuentra las 10 canciones mejor rankeadas en 2010. Muestra el ranking, el nombre del grupo y el nombre de la cancion, pero no muestres la misma cancion dos veces. Ordena el resultado por ranking en orden ascendente.

### TABLA

billboard_top_100_year_end

| year | year_rank | group_name    | artist        | song_name                                | id  |
| ---- | --------- | ------------- | ------------- | ---------------------------------------- | --- |
| 1956 | 1         | Elvis Presley | Elvis Presley | Heartbreak Hotel                         | 1   |
| 1956 | 2         | Elvis Presley | Elvis Presley | Don't Be Cruel                           | 2   |
| 1956 | 3         | Nelson Riddle | Nelson Riddle | Lisbon Antigua                           | 3   |
| 1956 | 4         | Platters      | Platters      | My Prayer                                | 4   |
| 1956 | 5         | Gogi Grant    | Gogi Grant    | The Wayward Wind                         | 5   |
| 1956 | 6         | Les Baxter    | Les Baxter    | The Poor People Of Paris                 | 6   |
| 1956 | 7         | Doris Day     | Doris Day     | Whatever Will Be Will Be (Que Sera Sera) | 7   |

# 💻 RESPUESTA

```sql
SELECT
    DISTINCT song_name,
    year_rank,
    group_name
FROM billboard_top_100_year_end
WHERE year = 2010
ORDER BY year_rank ASC
LIMIT 10;
```

# 📊 Explicación

Primero se filtran los registros del anio `2010` con `WHERE year = 2010`. Luego `DISTINCT` evita repetir la misma combinacion de cancion, ranking y grupo.

Despues `ORDER BY year_rank ASC` deja las canciones ordenadas desde la mejor posicion y `LIMIT 10` conserva solo las diez primeras del ranking.
