# Artist Appearance Count

## PROBLEMA

**[ENG]**
Find how many times each artist appeared on the Spotify ranking list. Output the artist name along with the corresponding number of occurrences. Order records by the number of occurrences in descending order.

**[ESP]**
Encuentra cuantas veces aparecio cada artista en la lista de ranking de Spotify. Muestra el nombre del artista junto con su numero de apariciones. Ordena los resultados por la cantidad de apariciones en orden descendente.

---

### TABLA

`spotify_worldwide_daily_song_ranking`

Tabla de ejemplo omitida por extension.

---

## RESPUESTA

```sql
SELECT
    artist,
    COUNT(*) AS n_occurrences
FROM spotify_worldwide_daily_song_ranking
GROUP BY artist
ORDER BY n_occurrences DESC;
```

---

## EXPLICACION

La consulta agrupa los registros por `artist`, de forma que cada grupo represente todas las apariciones de un mismo artista en el ranking.

Despues `COUNT(*)` cuenta cuantas filas tiene cada grupo y `ORDER BY n_occurrences DESC` ordena el resultado desde el artista con mas apariciones hasta el que tiene menos.
