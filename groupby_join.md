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
SELECT COUNT(*) AS `num_of_degrees`, `degrees`.`department_id` AS `department_id` FROM `degrees` GROUP BY `department_id`;
```

## Seleziono tutti gli studenti iscritto al Corso di Laurea in Economia
```sql
SELECT students.*, `degrees`.`name` AS `degree_name`
FROM students
JOIN degrees
ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` LIKE 'Corso di Laurea in Economia';
```

## Seleziono tutti i Corsi di Laurea Magistrale del Dipartimento di NeuroScienze
```sql
SELECT degrees.*, `departments`.`name` AS `department_name`
FROM degrees
JOIN departments
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` LIKE 'Dipartimento di Neuroscienze' AND `degrees`.`level` LIKE 'magistrale';
```

## Seleziono tutti i corsi in cui insegna Fulvio Amato
```sql
SELECT `courses`.`name` AS `course_name` , `teachers`.`name`, `teachers`.`surname`
FROM course_teacher
JOIN courses
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN teachers 
ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = 44;
```
