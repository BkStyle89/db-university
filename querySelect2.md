<----------------------------------------------------------------------------------->

## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia*

select degrees.id, degrees.name as degree_name, degrees.level,students.id as student_id, students.name, students.surname 
from students
join degrees on `students`.`degree_id` = `degrees`.`id`
where `degrees`.`name` = "Corso di Laurea in Economia"

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze*

select degrees.id, degrees.name, degrees.level, departments.id, departments.name as department_name
from degrees
join `departments` on `degrees`.`department_id` = `departments`.`id`
where `departments`. `name` = "Dipartimento di Neuroscienze"


## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)*

select teachers.id, teachers.name, teachers.surname, courses.name as courses_name, courses.period, courses.year, courses. cfu
from teachers
join course_teacher on teachers.id =course_teacher.teacher_id
join courses on course_teacher.course_id= courses.id
where teachers.id = 44