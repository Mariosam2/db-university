## Conto quanti iscritti ci sono stati ogni anno
```sql
SELECT COUNT(*) AS num_of_enroled, YEAR(`students`.`enrolment_date`) AS enrolment_year FROM students GROUP BY enrolment_year;
```