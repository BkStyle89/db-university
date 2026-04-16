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

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

select students.name, students.surname, degrees.name as degree_name, degrees.level, departments.name as departments_name
from students
join degrees on students.degree_id = degrees.id
join departments on degrees.department_id=departments.id
order by name asc


## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti*

select degrees.name as corso_di_laurea, degrees.level, courses.name as course_name, courses.description, courses.period, courses.year, courses.cfu, teachers.id as teacher_id, teachers.name as teacher_name, teachers.surname as teacher_surname
from degrees
join courses on degrees.id = courses.id
join course_teacher on courses.id = teacher_id
join teachers on course_teacher.teacher_id = teachers.id