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

## Seleziono tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```sql
SELECT  `students`.`name` AS `student_name`, `students`.`surname` AS `student_surname`, degrees.*, `departments`.`name` AS `department_name`
FROM students
JOIN degrees
ON `students`.`degree_id` = `degrees`.`id`
JOIN departments
ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`;
```

## Seleziono tutti i corsi di laurea con i relativi corsi e insegnanti
```sql
SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS course_name, `teachers`.`name` AS teacher_name, `teachers`.`surname` AS teacher_surname
FROM degrees
JOIN courses
ON `degrees`.`id` = `courses`.`degree_id`
JOIN course_teacher 
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN teachers 
ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

## Seleziono tutti i docenti che insegnano nel Dipartimento di Matematica (54)
```sql
SELECT teachers.*, `departments`.`name`
FROM teachers
JOIN course_teacher
ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN courses
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN degrees
ON `courses`.`degree_id` = `degrees`.`id`
JOIN departments 
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` LIKE 'Dipartimento di Matematica';
```

## BONUS: Seleziono per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
```sql
SELECT `students`.`name`, `students`.`surname`, COUNT(exam_id) AS `num_of_attempts`, `courses`.`name`
FROM exam_student
JOIN students
ON `exam_student`.`student_id` = `students`.`id`
JOIN exams
ON `exam_student`.`exam_id` = `exams`.`id`
JOIN courses 
ON `exams`.`course_id` = `courses`.`id`
GROUP BY `courses`.`id`, `students`.`id`;
/* Prova */
SELECT `students`.`name`, `students`.`surname`, COUNT(exam_id) AS num_of_attempts, `courses`.`name`
FROM students
JOIN exam_student ON `students`.`id` = `exam_student`.`student_id`
JOIN exams ON `exam_student`.`exam_id` = `exams`.`id`
JOIN courses ON `exams`.`course_id` = `courses`.`id`
GROUP BY `students`.`id`, `courses`.`id`;
```