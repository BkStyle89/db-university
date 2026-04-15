
<--------------------------------------------------------------------------------------------->

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

<--------------------------------------------------------------------------------------------->

## Table name Student

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- name (VARCHAR(15) NOTNULL)
- surname (VARCHAR(15) NOTNULL)
- email (CHAR(30) NOTNULL)
- phone (CHAR(13) NOTNULL)
- adress (TINYINT NOTNULL)
- class_choice (VARCHAR(15) NULL)
- date_of_birth (DATE NOTNULL)

## Table name Teacher

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- name (VARCHAR(15) NOTNULL)
- surname (VARCHAR(15) NOTNULL)
- email (CHAR(30) NOTNULL)
- phone  (CHAR(13) NOTNULL)

## Table name Exam

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- sessions (VARCHAR(5) NOTNULL)
- subjects (VARCHAR(15) NOTNULL)

## Table name university

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- location (TINYINIT NOTNULL)

## Table name university Department

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- type (VARCHAR(15) NOTNULL)
- location (SMALLINIT NOTNULL)
- university_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX

## Table name course

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- class (VARCHAR(2) NOTNULL)
- year (TINYINT NOTNULL)
- department_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX
- start_date (DATE NOTNULL)
- end_date (DATE NOTNULL)

## Table name specialization

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- course_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX
- type_of_specialization (VARCHAR(15) NOTNULL)

## Table name course_specialization

- id ( PK BIGINT AI UNIQUE NOTNULL) INDEX
- specialization_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX
- course_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX

## Table name student_exam

- student_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX
- exam_id ( FK BIGINT AI UNIQUE NOTNULL) INDEX
- vote (VARCHAR(1) NULL)
- result (VARCHAR(10) NULL)


## Data Query students from 1990*

select *
from students
WHERE YEAR (date_of_birth) = 1990;