## Seleziono tutti gli studenti nati nel 1990 (160)
```sql
SELECT * FROM `students` WHERE year(`date_of_birth`) = 1990;
```

## Seleziono tutti i corsi che valgono più di 10 crediti (479)
```sql
SELECT * FROM `courses` WHERE `cfu` > 10;
```

## Seleziono tutti gli studenti che hanno più di 30 anni
```sql
SELECT * FROM `students` WHERE year(NOW()) - year(`date_of_birth`) > 30;
```

## Seleziono tutti i corsi del primo semestre del primo anno (286)
```sql
SELECT * FROM `courses` WHERE `period` LIKE 'I semestre' AND `year` = 1;
```

## Seleziono gli esami che avvengono dalle 14 in poi del 20/06/2020 (21)
```sql
SELECT * FROM `exams` WHERE `date` LIKE '2020-06-20' AND HOUR(`hour`) >= 14;
```

## Seleziono tutti i corsi di laurea magistrale(38)

```sql
SELECT * FROM `degrees` WHERE `level`
 LIKE 'magistrale';
```

## Numero di dipartimenti(12)
```sql
SELECT COUNT(*) as `num_of_departments` FROM `departments`;
```


## Seleziono tutti gli insegnanti senza numero di telefono 
```sql
SELECT * FROM `teachers` WHERE `phone` IS null;
```