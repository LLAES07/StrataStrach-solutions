# Gender With Most Doctor Appointments

## 📌 PROBLEMA

**[ENG]**
Find the gender that has made the most number of doctor appointments.
Output the gender along with the corresponding number of appointments.

**[ESP]**
Encuentra el genero que ha hecho el mayor numero de citas al doctor.
Muestra el genero junto con el numero de citas correspondientes.

# TABLA

medical_appointments

|patientid|appointmentid|gender|scheduledday|appointmentday|age|neighbourhood|scholarship|hipertension|diabetes|alcoholism|handcap|sms_received|no_show|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|914121144686824|5709776|M|2016-05-17 14:29:43|2016-06-03|3|JARDIM CAMBURI|0|0|0|0|0|1|Yes|
|54921576586|5551813|F|2016-04-06 14:45:46|2016-05-09|31|MARIA ORTIZ|0|0|0|0|0|0|Yes|
|52587225747632|5649314|F|2016-05-02 19:01:13|2016-05-12|66|SANTOS DUMONT|0|0|0|0|0|1|Yes|
|6769994598599|5663542|M|2016-05-05 10:12:16|2016-05-05|21|TABUAZEIRO|0|0|0|0|0|0|No|

# 💻 RESPUESTA

```sql
SELECT
    gender,
    COUNT(appointmentid) AS total_appointments
FROM medical_appointments
GROUP BY gender
ORDER BY total_appointments DESC;
```

# 📊 Explicación

Para saber que genero tiene mas citas, la consulta agrupa los registros por `gender`. Luego `COUNT(appointmentid)` cuenta cuantas citas hay en cada grupo.

Finalmente, `ORDER BY total_appointments DESC` ordena el resultado de mayor a menor para dejar primero el genero con mas appointments.
