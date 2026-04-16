<----------------------------------------------------------------------------------->

## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia*

select degrees.id, degrees.name as degree_name, degrees.level,students.id as student_id, students.name, students.surname 
from students
join degrees on `students`.`degree_id` = `degrees`.`id`
where `degrees`.`name` = "Corso di Laurea in Economia"