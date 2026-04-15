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