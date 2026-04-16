<-------------------------------------------------------------------------------------->

## Data Query students from 1990*

select *
from students
WHERE YEAR (date_of_birth) = 1990;


## Data Query of CFU bigger than 10*

select *
from courses
WHERE cfu >= 10;

## Data query of  first semester and first year*

select *
from courses
WHERE period = 'I semestre'
	AND year = 1;

## Data query of students age = 30*

select date_of_birth,
	timestampdiff(YEAR,date_of_birth,curdate()) AS age
from students
WHERE timestampdiff(YEAR,date_of_birth,curdate()) = 30;


## Data query of exams from 20/06/2020 after 14:00pm*

select *
from exams
WHERE date = '2020-06-20'
	AND hour > '14:00:00';


## Data query for Corsi di Laurea Magistrale*

select *
from degrees
where level = 'magistrale';

## Data query for departments*

select count(*) AS number
from departments


## Data query for null phone*

select count(*) as number
from teachers
where phone is null

## Data query for group by cfu & name*

select count(id) as `total_courses` , `cfu`, `name`
from courses
group by `cfu`, `name`;

## Data query for group by cfu*

select count(id) as `total_courses` , `cfu`
from courses
group by cfu;

## Data query for year of birth of students*

select count(id) as `total_students`, year(`date_of_birth`) as `year_of_birth`
from students
group by `date_of_birth`


## Data query voto più basso d'esame*

select exam_id, MIN(vote) AS voto_minimo
from exam_student
group by exam_id

## Data query corso di laurea in informatica*

select  `courses`.`id`,`courses`.`name`,`courses`.`period`,`courses`.`cfu`,`courses`.`year`,`courses`.`website`,`degrees`.`name`as degree_name
from `courses`
join `degrees` on `courses`.`degree_id` = `degrees`.`id`
Where `degrees`.`name` = "Corso di Laurea in Informatica"

## Data query informazioni id 144 appelli esame*

select `courses`.`name`,`courses`.`period`,`courses`.`year`,`courses`.`cfu`,`exams`.`course_id`
from courses
join `exams` on `courses`.`id` = `exams`.`course_id`
where course_id = 144


## Data query dipartimento economia*
select *
from degrees
join `departments` on `degrees`.`department_id`= `departments`.`id`
where `degrees`.`name` = "Corso di Laurea in Diritto dell'Economia"

## Data query appelli d'esame del Corso di Laurea Magistrale in Fisica*

select *
from exams
inner join `courses` on `exams`.`course_id` = `courses`.`id`
inner join `degrees` on `courses`. `degree_id` = `degrees`.`id`
where `degrees`.`name` = "Corso di Laurea Magistrale in Fisica"
	AND `courses`.`year`= 1

## Data query docenti che insegnano nel Corso di Laurea in Lettere*

select distinct teachers.name, teachers.surname
from teachers
join course_teacher on teachers.id = course_teacher.teacher_id
join courses on course_teacher.course_id = courses.id
join degrees on degrees.id = courses.degree_id
where degrees.name ="Corso di Laurea in Lettere";

## Data query voto medio di superamento d'esame per ogni corso, con anche i dati del corso di laurea associato, ordinati per media voto decrescente*

select avg(exam_student.vote) as media, courses.name as course_name, degrees.name as degree_name
from exam_student
join exams on exam_student.exam_id=exams.id
join courses on exams.course_id= courses.id
join degrees on courses.degree_id = degrees.id
where exam_student.vote >= 18
group by courses.id
order by media desc


