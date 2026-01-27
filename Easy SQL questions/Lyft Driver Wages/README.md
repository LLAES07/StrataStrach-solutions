Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD. Output all details related to retrieved records.

### Table

lyft_drivers

|index|start_date|end_date|yearly_salary|
|---|---|---|---|
|0|2018-04-02||48303|
|1|2018-05-30||67973|
|2|2015-04-05||56685|
|3|2015-01-08||51320|
|4|2017-03-09||67507|
|5|2015-09-07||55155|
|6|2016-05-22|2018-08-06|35847|
|7|2015-09-29|2018-07-20|46974|
|8|2015-09-15|2019-04-30|54316|


# RESPUESTA

```sql
SELECT
    *
FROM lyft_drivers
WHERE
    -- Condición de filtro
    yearly_salary <= 30000 OR 
    yearly_salary > 70000;

```