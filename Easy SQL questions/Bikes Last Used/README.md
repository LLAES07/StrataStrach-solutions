Find the last time each bike was in use. Output both the bike number and the date-timestamp of the bike's last use (i.e., the date-time the bike was returned). Order the results by bikes that were most recently used.}

# TABLA
### dc_bikeshare_q1_2012

|duration|duration_seconds|start_time|start_station|start_terminal|end_time|end_station|end_terminal|bike_number|rider_type|id|
|---|---|---|---|---|---|---|---|---|---|---|
|0h 10m 47sec.|647|2012-03-25 10:30:00|17th & Corcoran St NW|31214|2012-03-25 10:40:00|Calvert St & Woodley Pl NW|31106|W00576|Registered|326188|
|0h 11m 45sec.|705|2012-03-28 18:59:00|Rosslyn Metro / Wilson Blvd & Ft Myer Dr|31015|2012-03-28 19:11:00|21st & M St NW|31212|W00011|Registered|345585|
|0h 7m 45sec.|465|2012-03-12 22:30:00|3rd & H St NE|31616|2012-03-12 22:37:00|Florida Ave & R St NW|31503|W01215|Registered|251919|
|0h 4m 27sec.|267|2012-03-12 20:11:00|14th & G St NW|31238|2012-03-12 20:15:00|14th & Rhode Island Ave NW|31203|W00455|Registered|251426|
|0h 10m 2sec.|602|2012-02-03 09:06:00|Lamont & Mt Pleasant NW|31107|2012-02-03 09:16:00|17th & Rhode Island Ave NW|31239|W00300|Registered|105965|
|0h 24m 59sec.|1499|2012-03-30 19:35:00|Eastern Market Metro / Pennsylvania Ave & 7th St SE|31613|2012-03-30 20:00:00|Massachusetts Ave & Dupont Circle NW|31200|W01352|Registered|357661|
|0h 13m 45sec.|825|2012-03-10 16:44:00|North Capitol St & F St NW|31624|2012-03-10 16:58:00|Thomas Circle|31241|W00089|Registered|240483|



```sql


-- FILTER: LAST TIME EACH BIKE WAS USE IT 
-- SELECT bike_number, and date time last use
-- ORDER bt bikes last used

--1. Encontrar la ultima vez que cada bicicleta fue usada

SELECT
    bike_number,
    MAX(end_time) AS last_time_used
FROM dc_bikeshare_q1_2012

GROUP BY
    bike_number
ORDER BY
    last_time_used DESC
    

```