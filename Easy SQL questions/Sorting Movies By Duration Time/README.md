# Sorting Movies By Duration Time


**[ENG]**

You have been asked to sort movies according to their duration in descending order.


Your output should contain all columns sorted by the movie duration in the given dataset.


**[ES]**

Te han solicitado ordenar las peliculas según su duración en orden descendente.

Tu consulta debe mostrar todas las columnas ordenadas por la duración de la película.

### TABLA



|show_id|title|release_year|rating|duration|
|---|---|---|---|---|
|s1|Dick Johnson Is Dead|2020|PG-13|90 min|
|s95|Show Dogs|2018|PG|90 min|
|s108|A Champion Heart|2018|G|90 min|
|s163|Marshall|2017|PG-13|118 min|
|s174|Snervous Tyler Oakley|2015|PG-13|83 min|
|s346|Open Season: Scared Silly|2015|PG|85 min|
|s583|Mother's Day|2016|PG-13|118 min|
|s600|The Best of Enemies|2019|PG-13|133 min|
|s925|Aliens Stole My Body|2020|PG|88 min|
|s1036|The Zookeeper's Wife|2017|PG-13|127 min|
|s1204|The BFG|2016|PG|118 min|
|s1219|YES DAY|2021|PG|90 min|
|s1242|Moxie|2021|PG-13|112 min|
|s1289|Operation Finale|2018|PG-13|123 min|
|s1500|The Midnight Sky|2020|PG-13|119 min|
|s1537|Incarnate|2016|PG-13|87 min|
|s1561|The Prom|2020|PG-13|132 min|
|s1577|Bobbleheads The Movie|2020|PG|83 min|
|s1690|Loving|2016|PG-13|124 min|
|s1704|Jingle Jangle: A Christmas Journey|2020|PG|124 min|
|s1887|David Attenborough: A Life on Our Planet|2020|PG|84 min|
|s1901|Vampires vs. the Bronx|2020|PG-13|86 min|
|s2331|Eurovision Song Contest: The Story of Fire Saga|2020|PG-13|124 min|
|s2560|Becoming|2020|PG|89 min|
|s2573|Roped|2020|PG|90 min|
|s2679|Jem and the Holograms|2015|PG|119 min|
|s2755|Greater|2016|PG|131 min|
|s2912|A Shaun the Sheep Movie: Farmageddon|2019|G|87 min|
|s2934|Polaroid|2019|PG-13|88 min|
|s2989|Menashe|2017|PG|82 min|
|s3081|Benchwarmers 2: Breaking Balls|2019|PG-13|90 min|
|s3103|Sweetheart|2019|PG-13|83 min|
|s3189|A Cinderella Story: Christmas Wish|2019|PG|86 min|
|s3384|Echo in the Canyon|2019|PG-13|82 min|
|s3392|The Command|2018|PG-13|118 min|
|s3583|Selfless|2015|PG-13|117 min|
|s3873|Knock Down The House|2019|PG|88 min|
|s4493|Gnome Alone|2018|PG|86 min|
|s4538|The Black Prince|2017|PG-13|121 min|
|s4820|Brain on Fire|2016|PG-13|89 min|
|s4874|Pup Star: World Tour|2018|G|87 min|
|s5124|Pottersville|2017|PG-13|86 min|
|s5199|SPF-18|2017|PG-13|75 min|
|s5274|Ghost of the Mountains|2017|G|78 min|
|s5488|Wild Oats|2016|PG-13|86 min|
|s5597|Growing Up Wild|2016|G|78 min|
|s5646|Marvel's Hulk: Where Monsters Dwell|2016|PG|75 min|
|s5866|Marvel Super Hero Adventures: Frost Fight!|2015|PG|74 min|
|s6114|Aliens Ate My Homework|2018|PG|90 min|


# RESPUESTA

```sql
SELECT
    *
FROM movie_catalogue
ORDER BY duration DESC  

```