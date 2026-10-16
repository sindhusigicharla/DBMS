CREATE DATABASE outer_join_demo;

USE outer_join_demo;

CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    course_id INT
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50)
);

CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    fee DECIMAL(8,2)
);

INSERT INTO students
VALUES
(1, 'Ravi', 101),
(2, 'Priya', 102),
(3, 'Kiran', 103),
(4, 'Sita', NULL),
(5, 'Arjun', 105);


INSERT INTO courses
VALUES
(101, 'Java'),
(102, 'Python'),
(103, 'SQL'),
(104, 'React'),
(106, 'Cloud Computing');

INSERT INTO enrollments
VALUES
(1, 1, 5000.00),
(2, 2, 6000.00),
(3, 4, 4500.00),
(4, 6, 7000.00);


select * from students;
select * from courses;
select * from enrollments;


-- Right join
SELECT
    s.student_id,
    s.student_name,
    c.course_id,
    c.course_name
FROM students s
RIGHT JOIN courses c
    ON s.course_id = c.course_id;
    
-- Left join

SELECT
    s.student_id,
    s.student_name,
    s.course_id,
    c.course_name
FROM students s
LEFT JOIN courses c
    ON s.course_id = c.course_id;
    
-- Full outer join 


SELECT s.student_id, s.student_name, s.course_id, c.course_name
FROM students s LEFT JOIN courses c ON s.course_id = c.course_id
UNION

SELECT s.student_id, s.student_name, c.course_id, c.course_name
FROM students s RIGHT JOIN courses c ON s.course_id = c.course_id;

-- Display all students along with their course names, 
-- including students who are not assigned to any course.

select student_name, course_name from students as s
left join courses as c on s.course_id = c.course_id;


-- Display all students and their course IDs, 
-- including students whose course does not exist in the courses table.

select student_name, course_name, s.course_id from students as s
left join courses as c on s.course_id = c.course_id;


-- Find students who are not assigned to a valid course.
select student_name from students as s left join courses as c
on s.course_id = c.course_id
where course_name is null;
;

-- Display all students with their enrollment fees, including students who have not enrolled.
select student_name, enrollment_id, fee from students as s left join 
enrollments as e on  s.student_id = e.student_id ;



-- Display all courses and the names of students assigned to them, 
-- including courses with no students.
select student_name, course_name from students as s right join courses as c
on s.course_id = c.course_id;

-- Find courses that have no students assigned to them.

select course_name, student_name from students as s right join courses as c 
on s.course_id = c.course_id where student_name is null;

-- Display all courses with the student IDs and names, including courses that have no matching student.

-- Display all students and all courses, including unmatched records on both sides.

-- Display every student and every course, showing the IDs and names from both tables.

-- Display only unmatched students and unmatched courses — exclude records where a student has a matching course.

select student_id, c.course_id from students as s left join courses as c
on s.course_id = c.course_id where c.course_id is null
union
select student_id , c.course_id from students as s right join courses as c
on s.course_id = c.course_id where student_id is null;
