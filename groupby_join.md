## Conto quanti iscritti ci sono stati ogni anno
```sql
SELECT COUNT(*) AS `num_of_enroled`, YEAR(`students`.`enrolment_date`) AS `enrolment_year` FROM `students` GROUP BY `enrolment_year`;
```

## Conto gli insegnanti che hanno l'ufficio nello stesso edificio
```sql
SELECT COUNT(*) AS `num_of_teachers`, `teachers`.`office_address` FROM `teachers` GROUP BY `teachers`.`office_address`;
```

## Calcolo la media dei voti di ogni appello d'esame
```sql
SELECT AVG(`exam_student`.`vote`) AS `avg_votes` FROM `exam_student`;
```

## Conto quanti corsi di laurea ci sono per ogni dipartimento
```sql
SELECT COUNT(*) AS `num_of_degrees`, `degrees`.`department_id` AS `dep_id` FROM `degrees` GROUP BY `dep_id`;
```