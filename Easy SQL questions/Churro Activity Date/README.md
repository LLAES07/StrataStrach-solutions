# Churro Activity Date


## ðŸ“Œ PROBLEMA


**[ENG]**

Find the inspection date and risk category (pe_description) of facilities named 'STREET CHURROS' that received a score below 95.

**[ESP]**

Encuentra la fecha de inspecciÃ³n y la categorÃ­a de riesgo (pe_description)  de los locales llamados 'STREET CHURROS' que recibieron un puntaje inferior a 95.



## TABLA 

### los_angeles_restaurant_health_inspections


| serial_number | activity_date | facility_name    | score | grade | service_code | service_description | employee_id | facility_address     | facility_city | facility_id | facility_state | facility_zip | owner_id  | owner_name            | pe_description                        | program_element_pe | program_name     | program_status | record_id |
| ------------- | ------------- | ---------------- | ----- | ----- | ------------ | ------------------- | ----------- | -------------------- | ------------- | ----------- | -------------- | ------------ | --------- | --------------------- | ------------------------------------- | ------------------ | ---------------- | -------------- | --------- |
| DAQHRSETQ     | 2017-06-08    | MARGARITAS CAFE  | 93    | A     | 1            | ROUTINE INSPECTION  | EE0000006   | 5026 S CRENSHAW BLVD | LOS ANGELES   | FA0023656   | CA             | 90043        | OW0004133 | BAZAN, ASCENCION      | RESTAURANT (61-150) SEATS HIGH RISK   | 1638               | MARGARITAS CAFE  | ACTIVE         | PR0011718 |
| DA2GQRJOS     | 2017-03-07    | LAS MOLENDERAS   | 97    | A     | 1            | ROUTINE INSPECTION  | EE0000997   | 2635 WHITTIER BLVD   | LOS ANGELES   | FA0160416   | CA             | 90023        | OW0125379 | MARISOL FEREGRINO     | RESTAURANT (0-30) SEATS HIGH RISK     | 1632               | LAS MOLENDERAS   | INACTIVE       | PR0148504 |
| DAMQTA46T     | 2016-03-22    | SANDRA'S TAMALES | 93    | A     | 1            | ROUTINE INSPECTION  | EE0001049   | 5390 WHITTIER BLVD   | LOS ANGELES   | FA0171769   | CA             | 90022-4032   | OW0178828 | SANDRA'S TAMALES INC. | RESTAURANT (0-30) SEATS MODERATE RISK | 1631               | SANDRA'S TAMALES | ACTIVE         | PR0164225 |

# ðŸ’» RESPUESTA

```sql

SELECT
    activity_date,
    pe_description
FROM 
    los_angeles_restaurant_health_inspections
WHERE
    LOWER(facility_name) ~ '^street churros' 
    AND
    score < 95;
```

# EXPLICACION

Primero se filtran los registros por fecha de actividad para quedarnos solo con los dias relevantes. Luego se agrupan o cuentan los eventos en esa fecha para obtener la actividad del dia solicitado.

Asi se responde con una sola fecha o con el conjunto de fechas que cumplen la condicion, manteniendo la consulta enfocada unicamente en los registros que pertenecen al periodo pedido.
