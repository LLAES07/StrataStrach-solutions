# Gender With Most Doctor Appointments

## PROBLEMA

**[ENG]**
Find the gender that has made the most number of doctor appointments. Output the gender along with the corresponding number of appointments.

**[ESP]**
Encuentra el genero que ha realizado la mayor cantidad de citas medicas. Muestra el genero junto con el numero de citas correspondiente.

---

### TABLA

`medical_appointments`

|patientid|appointmentid|gender|scheduledday|appointmentday|age|neighbourhood|scholarship|hipertension|diabetes|alcoholism|handcap|sms_received|no_show|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|914121144686824|5709776|M|2016-05-17 14:29:43|2016-06-03|3|JARDIM CAMBURI|0|0|0|0|0|1|Yes|
|54921576586|5551813|F|2016-04-06 14:45:46|2016-05-09|31|MARIA ORTIZ|0|0|0|0|0|0|Yes|
|52587225747632|5649314|F|2016-05-02 19:01:13|2016-05-12|66|SANTOS DUMONT|0|0|0|0|0|1|Yes|
|6769994598599|5663542|M|2016-05-05 10:12:16|2016-05-05|21|TABUAZEIRO|0|0|0|0|0|0|No|

---

## RESPUESTA

```sql
SELECT
    gender,
    COUNT(appointmentid) AS total_appointments
FROM medical_appointments
GROUP BY gender
ORDER BY total_appointments DESC;
```

---

## EXPLICACION

La consulta agrupa las filas por `gender`, de modo que cada grupo represente un genero distinto.

Luego `COUNT(appointmentid)` cuenta cuantas citas hay en cada grupo. Finalmente `ORDER BY total_appointments DESC` deja primero el genero con mayor cantidad de citas.
