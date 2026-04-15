# Dirty Hotel Rooms


**[ENG]**

Find hotels in the Netherlands that got complaints from guests about room dirtiness (word "dirty" in its negative review). Output all the columns in your results

**[ES]**

Encuentra los hoteles en holanda que tengan quejas de los huespedes acerca de la suciedad en las piezas ("dirty" en su review negativa). Muestra todas las columnas en tus resultados.

### Table

hotel_reviews


|hotel_address|additional_number_of_scoring|review_date|average_score|hotel_name|reviewer_nationality|negative_review|review_total_negative_word_counts|total_number_of_reviews|positive_review|review_total_positive_word_counts|total_number_of_reviews_reviewer_has_given|reviewer_score|tags|days_since_review|lat|lng|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|7 Western Gateway Royal Victoria Dock Newham London E16 1AA United Kingdom|359|2017-07-05|8.5|Novotel London Excel|United Kingdom|coffee and tea at breakfast were not particularly hot Otherwise everything else was fine|16|1158|we were allocated the newly refurbished rooms and so everything was fresh and the bed was very comfortable the hotel is ideally situated near City Airport although eventually we travelled by train|34|2|10|[' Leisure trip ', ' Family with young children ', ' Standard Double Room with Two Single Beds ', ' Stayed 2 nights ', ' Submitted from a mobile device ']|29 days|51.51|0.02|
|35 Charles Street Mayfair Westminster Borough London W1J 5EB United Kingdom|252|2015-08-29|9.1|The Chesterfield Mayfair|Israel|No Negative|0|1166|We liked everything The hotel is simply a boutique the staff were all polite and helpfull The room was clean and been serviced daily Wifi was completely free Breakfast was simply great I so much want to get back|41|8|10|[' Leisure trip ', ' Couple ', ' Classic Double Room ', ' Stayed 4 nights ', ' Submitted from a mobile device ']|705 day|51.51|-0.15|
|14 Rue Stanislas 6th arr 75006 Paris France|40|2017-05-23|9.1|Hotel Le Six|United States of America|There is currently utility construction taking place on the street in front of the hotel so a little noisy at times and barriers in place|27|177|Neat boutique hotel Some of the most comfortable hotel beds I have ever come across Staff was wonderful Loved the location Not too touristy Luxembourg gardens close by and a great place for a morning run walk|39|3|9.2|[' Leisure trip ', ' Family with young children ', ' Deluxe Double Room ', ' Stayed 4 nights ', ' Submitted from a mobile device ']|72 days|48.84|2.33|
|Gran V a De Les Corts Catalanes 570 Eixample 08011 Barcelona Spain|325|2016-08-25|8.2|Sunotel Central|United Kingdom|Coffee at breakfast could be better When you spend this amount in a hotel I expect better coffee in the morning|22|3870|Great bed nice to have a coffee machine in the room love the air conditioning and basically loved the attitude of the staff Really great|26|2|9.2|[' Leisure trip ', ' Group ', ' Comfort Double or Twin Room ', ' Stayed 1 night ', ' Submitted from a mobile device ']|343 day|41.38|2.16|
|Rathausstra e 17 01 Innere Stadt 1010 Vienna Austria|195|2015-09-17|8.5|Austria Trend Hotel Rathauspark Wien|United Kingdom|A bit out of the way location wise|9|1884|Clean modern rooms and bathroom well equipped|9|2|7.5|[' Leisure trip ', ' Couple ', ' Comfort Room ', ' Stayed 2 nights ', ' Submitted from a mobile device ']|686 day|48.21|16.36|
|100 110 Euston Road Camden London NW1 2AJ United Kingdom|728|2016-02-28|8.9|Pullman London St Pancras|United Kingdom|No pool|3|3168|Breakfast|2|1|8.8|[' Business trip ', ' Solo traveler ', ' Classic King Room ', ' Stayed 1 night ', ' Submitted from a mobile device ']|522 day|51.53|-0.13|
|12 Folgate Street City of London London E1 6BX United Kingdom|197|2016-11-28|9.4|Batty Langley s|United Kingdom|Couldn t fault anything about this hotel|9|644|Plush luxurious room with excellent friendly staff|9|2|10|[' Leisure trip ', ' Couple ', ' Superior Double Room ', ' Stayed 1 night ', ' Submitted from a mobile device ']|248 day|51.52|-0.08|
|252 High Holborn Holborn Camden London WC1V 7EN United Kingdom|256|2017-01-13|9.4|Rosewood London|Australia|Nothing|2|1008|Best bat in London|5|1|9.6|[' Leisure trip ', ' Family with young children ', ' Executive King Room ', ' Stayed 5 nights ', ' Submitted from a mobile device ']|202 day|51.52|-0.12|

# REPSUESTA

```sql


SELECT
    *
FROM hotel_reviews
WHERE
    reviewer_nationality = 'Netherlands'
    AND
    negative_review LIKE '%dirty%';
```



# 📊 Explicación


Nos solicitan todos los datos para la nacionalidad `Netherlands` y con una review negativa que contiene dirty. Para esto usamos `WHERE` y  `LIKE` para lograr lo solicitado.