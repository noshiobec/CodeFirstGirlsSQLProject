# CodeFirstGirlsSQLProject
This is a database for an online learning platfrm. 
Disclaimer: The names and values used in this context are for illustration purposes only and are not based on any real-world data sets. 




DROP DATABASE IF EXISTS online_learning_db;
CREATE DATABASE IF NOT EXISTS online_learning_db;
USE online_learning_db;
CREATE TABLE  instructor (
	instr_id VARCHAR(10) NOT NULL,
    instr_fname VARCHAR (35) NOT NULL,
    instr_lname VARCHAR (35),
    instr_email VARCHAR (55),
    instr_phoneNo VARCHAR(45),
    instr_qualification VARCHAR (45),
    PRIMARY KEY (instr_id)
    );
CREATE TABLE courses (
	course_id VARCHAR(10) NOT NULL,
	course_name VARCHAR (35) NOT NULL,
    course_startDate DATE,
    course_duration INT(10) ,
    no_registration INT(10),
	rating DECIMAL (3,2),
    instr_id VARCHAR(10) NOT NULL,
    PRIMARY KEY (course_id),
    CONSTRAINT fk_instr_id FOREIGN KEY (instr_id) REFERENCES instructor (instr_id)
    );

CREATE TABLE students (
	student_id VARCHAR(10) NOT NULL,
    student_fname VARCHAR (35) NOT NULL,
    student_lname VARCHAR (35),
    email_address VARCHAR (35),
    phone_no VARCHAR(35),
    reg_date DATE,
    state VARCHAR(35),
    country VARCHAR(35),
    PRIMARY KEY (student_id)
    );
CREATE TABLE payments (
	payment_id INT(10) NOT NULL,
    amount FLOAT NOT NULL,
    payment_date DATE,
    payment_method VARCHAR(35),
    student_id VARCHAR(10),
    PRIMARY KEY (payment_id),
    CONSTRAINT fk_student_id FOREIGN KEY (student_id) REFERENCES students (student_id)
    );
CREATE TABLE registrations (
    student_id VARCHAR (10) NOT NULL,
    course_id VARCHAR(10) NOT NULL,
    registra_date DATE,
    PRIMARY KEY (student_id,course_id),
    CONSTRAINT fkreg_student_id FOREIGN KEY (student_id) REFERENCES students (student_id),
    CONSTRAINT fkreg_course_id FOREIGN KEY (course_id) REFERENCES courses (course_id)
    );
    
    INSERT INTO instructor (instr_id, instr_fname, instr_lname, instr_email, instr_phoneNo, instr_qualification)
VALUES
('t_1', 'John', 'Doe', 'johndoe@gmail.com', '+44 1234567890', 'PhD in Computer Science'),
('t_2', 'Jane', 'Smith', 'janesmith@gmail.com', '+1 1861234567', 'MA in English Literature'),
('t_3', 'Mark', 'Johnson', 'markjohnson@gmail.com', '+1 1861211212', 'Masters in Mathematics'),
('t_4', 'Emily', 'Davis', 'emilydavis@gmail.com', '+1 4161867890', 'Masters in Biology'),
('t_5', 'David', 'Lee', 'davidlee@gmail.com', '+44 2018632155', 'PhD in Physics'),
('t_6', 'Anna', 'Garcia', 'annagarcia@gmail.com', '+15141861212', 'Masters in History'),
('t_7', 'Michael', 'Brown', 'michaelbrown@gmail.com', '+1 6171867890', 'PhD in Psychology'),
('t_8', 'Sarah', 'Taylor', 'sarahtaylor@gmail.com', '+44 2042151212', 'MA in Sociology'),
('t_9', 'Thomas', 'Clark', 'thomasclark@gmail.com', '+1 2121861865', 'PhD in Economics'),
('t_10', 'Karen', 'White', 'karenwhite@gmail.com', '+1 3101861212', 'MA in Marketing');

INSERT INTO courses (course_id, course_name, course_startDate, course_duration, no_registration, rating, instr_id)
VALUES
('c_id1', 'Introduction to Computer Science', '2021-04-01', 120, 2, 4.5, 't_1'),
('c_id2', 'Sociology of Gender', '2023-01-01', 180, 8, 3.9, 't_8'),
('c_id3', 'Calculus I', '2023-02-01', 200, 10, 4.2, 't_3'),
('c_id4', 'Molecular Biology', '2022-07-01', 60, 7, 4.8, 't_4'),
('c_id5', 'Quantum Mechanics', '2021-08-01', 320, 9, 4.6, 't_5'),
('c_id6', 'Creative Writing', '2022-05-15', 45, 6, 4.0, 't_2'),
('c_id7', 'Social Psychology', '2023-01-01', 110, 11, 4.2, 't_7'),
('c_id8', 'Sociology', '2022-11-01', 130, 5, 3.9, 't_8'),
('c_id9', 'Microeconomics', '2022-01-01', 222, 10, 4.1, 't_9'),
('c_id10', 'Marketing Strategy', '2022-02-01', 67, 8, 4.7, 't_10'),
('c_id11', 'Data Structures and Algorithms', '2022-04-01', 55, 6, 4.5, 't_1'),
('c_id12', 'English Composition', '2023-02-15', 118, 3, 4.0, 't_2'),
('c_id13', 'Machine learning', '2021-06-01', 78, 9, 4.2, 't_3'),
('c_id14', 'Computer Vision', '2021-07-01', 95, 4, 4.8, 't_5'),
('c_id15', 'World History', '2023-02-01', 29, 3, 4.4, 't_6');

INSERT INTO students (student_id, student_fname, student_lname, email_address, phone_no, reg_date, state, country) 
VALUES
('s_1', 'Chong', 'Laan', 'chonglaan@gmail.com', '+86 3324572190', '2021-02-11', 'Shangai', 'China'),
('s_2', 'Becca', 'Smith', 'beccasmith@gmail.com', '+1 2025550163', '2021-11-01', 'Texas', 'USA'),
('s_3', 'David', 'Daniel', 'daviddaniel@gmail.com', '+234 7026739876', '2022-03-04', 'Lagos', 'Nigeria'),
('s_4', 'Sarah', 'Kayode', 'sarahkayode@gmail.com', '+1 3342675432', '2022-01-30', 'New York', 'USA'),
('s_5', 'Mike', 'Brown', 'mikebrown@gmail.com', '+44 7120230301', '2022-10-15', 'Dorset', 'United Kingdom'),
('s_6', 'vivian', 'Johnson', 'vivianjohnson@gmail.com', '+1 4166711234', '2023-02-08', 'Ontario', 'Canada'),
('s_7', 'Daniel', 'Adamu', 'danieladamu@gmail.com', '+234 8031234567', '2023-01-01', 'Abuja', 'Nigeria'),
('s_8', 'Lisa', 'Martins', 'lisamartins@gmail.com', '+1 2023117890', '2021-12-01', 'California', 'USA'),
('s_9', 'Jason', 'Garcia', 'jasongarcia@gmail.com', '+1 2022883210', '2022-09-21', 'Texas', 'USA'),
('s_10', 'eniola', 'Chen', 'eniolachen@gmail.com', '+234 9155565434', '2022-10-20', 'Benin', 'Nigeria'),
('s_11', 'Brian', 'Davis', 'briandavis@gmail.com', '+1 2026658901', '2022-11-01', 'California', 'USA'),
('s_12', 'Megan', 'Wilson', 'meganwilson@gmail.com', '+1 2024434567', '2022-03-19', 'Texas', 'USA'),
('s_13', 'Eric', 'Chang', 'ericchang@gmail.com', '+86 271234 5699', '2021-02-12', 'Beijing', 'China'),
('s_14', 'Julia', 'Moses', 'juliamoses@gmail.com', '+44 2665315678', '2021-08-01', 'California', 'USA'),
('s_15', 'Anthony', 'Mike', 'anthonymike@gmail.com', '+44 8736773210', '2022-01-11', 'Manchester', 'United Kingdom'),
('s_16', 'Melissa', 'Osaro', 'melissaosaro@gmail.com', '+1 2589999876', '2022-12-18', 'New York', 'USA'),
('s_17', 'Kevin', 'Daniel', 'kevindaniel@gmail.com', '+86 1012345678', '2023-02-16', 'Hong Kong', 'China'),
('s_18', 'Samantha', 'Kayode', 'samanthakayode@gmail.com', '+44 7709676543', '2021-09-28', 'Hull', 'United Kingdom');

INSERT INTO payments (payment_id, amount, payment_date, payment_method, student_id) 
VALUES
(1, 1200.00, '2021-07-15', 'Credit Card', 's_2'),
(2, 500.00, '2022-12-11', 'PayPal', 's_3'),
(3, 750.50, '2023-02-20', 'Bank Transfer', 's_1'),
(4, 1000.00, '2022-03-01', 'Credit Card', 's_5'),
(5, 500.00, '2022-11-18', 'PayPal', 's_6'),
(6, 750.00, '2023-01-01', 'Credit Card', 's_7'),
(7, 1000.00, '2022-09-14', 'Credit Card', 's_3'),
(8, 500.00, '2022-08-04', 'Credit Card', 's_9'),
(9, 750.00, '2022-11-30', 'Bank Transfer', 's_18'),
(10, 1000.50, '2021-07-11', 'Credit Card', 's_11'),
(11, 500.00, '2023-01-05', 'PayPal', 's_12'),
(12, 750.00, '2021-03-16', 'Bank Transfer', 's_13'),
(13, 1000.00, '2022-03-01', 'Credit Card', 's_3'),
(14, 500.00, '2021-12-30', 'PayPal', 's_15'),
(15, 750.60, '2021-03-28', 'Bank Transfer', 's_12'),
(16, 500.80, '2022-10-20', 'Bank Transfer', 's_12'),
(17, 750.00, '2021-09-19', 'Bank Transfer', 's_13'),
(18, 1300.00, '2022-11-01', 'PayPal', 's_3'),
(19, 500.99, '2021-03-17', 'PayPal', 's_15'),
(20, 750.00, '2022-07-24', 'Bank Transfer', 's_12');

INSERT INTO registrations (student_id, course_id, registra_date) 
VALUES
('s_1', 'c_id1', '2022-05-10'),
('s_2', 'c_id4', '2021-09-20'),
('s_3', 'c_id8', '2023-01-05'),
('s_4', 'c_id6', '2021-12-15'),
('s_5', 'c_id10', '2022-08-30'),
('s_6', 'c_id12', '2023-02-02'),
('s_7', 'c_id3', '2021-10-25'),
('s_8', 'c_id5', '2023-01-10'),
('s_9', 'c_id11', '2022-06-18'),
('s_10', 'c_id15', '2022-11-12'),
('s_11', 'c_id2', '2021-12-01'),
('s_12', 'c_id7', '2022-04-03'),
('s_13', 'c_id13', '2023-03-01'),
('s_14', 'c_id9', '2022-09-08'),
('s_15', 'c_id1', '2021-11-20'),
('s_16', 'c_id8', '2022-02-14'),
('s_17', 'c_id4', '2023-03-01'),
('s_18', 'c_id11', '2021-12-25');                        
                          
                          -- TASK CORE REQUIREMENTS
-- 1. ✔ Create relational DB of your choice with minimum 5 tables
-- 2. ✔ Set Primary and Foreign Key constraints to create relations between the tables
-- 3.Using any type of the joins create a view that combines multiple tables in a logical way
-- Problem question:  Names of students in USA, the courses offered by this set, and instructors taking this courses.
CREATE VIEW usa_students_details
AS
SELECT s.student_fname, s.student_lname, s.country, c.course_name, i.instr_fname
FROM students s
LEFT Join registrations r
ON s.student_id = r.student_id
JOIN courses c
ON r.course_id = c.course_id
JOIN instructor i
ON c.instr_id= i.instr_id
WHERE country = 'USA';

-- 4. ✔ In your database, create a stored function that can be applied toa query in your DB.
-- Problem Question: Checking for payments that are qualified or not qualified for discount.
DELIMITER !
CREATE FUNCTION discount_status(amount FLOAT(10))
RETURNS VARCHAR(30)
BEGIN
    DECLARE status VARCHAR(30);
    SET status = CASE
        WHEN amount > 750.00 THEN 'Qualified for discount'
        ELSE 'No discount needed'
    END;
    RETURN status;
END!
DELIMITER ;

SELECT discount_status(3000);

-- 5.✔ Prepare an example query with a subquery to demonstrate how to extract data from your DB for analysis
-- Formulated Question: A discunt of 25% is to be given to all students who made more than one payment and 
-- this discounted cost would reflect on their next purchase. Calclate the sum of this discounted value for this set of sudents. 
SELECT student_id, round(SUM(0.25*amount),2) as discounted_sum
FROM payments
WHERE student_id IN (SELECT s.student_id
FROM students s
JOIN payments p
ON s.student_id = p.student_id
GROUP BY s.student_id
HAVING COUNT(p.student_id) > 1)
GROUP BY student_id;

-- 6.✔ Create DB diagram where all table relations are shown


--  ---------- ADVANCED OPTIONS

-- 1. In your database, create a stored procedure and demonstrate how it runs
-- Get the courses taken by instructors with a phd qualification.
DELIMITER //
CREATE PROCEDURE phd_instr_courses()
BEGIN
	SELECT * FROM courses;
    SELECT c.course_name, i.instr_fname, i.instr_qualification
FROM courses c
JOIN instructor i
ON c.instr_id = i.instr_id
WHERE instr_qualification LIKE '%PhD%';
END//
DELIMITER ;

CALL phd_instr_courses;

-- 2.✔ In your database, create a trigger and demonstrate how it runs
-- A trigger to capitalize coursenames before being insertered. 

CREATE TRIGGER capitalize_course_name
BEFORE INSERT ON courses
FOR EACH ROW
SET NEW.course_name = UPPER(NEW.course_name);

INSERT INTO courses (course_id, course_name, course_startDate, course_duration, no_registration, rating, instr_id)
VALUES
('c_idtest', 'Testing My Trigger Creation', '2023-04-03', 120, 2, 5.0, 't_1');


-- 3.✔ In your database, create an event and demonstrate how it runs
--  Creating an event that returns total number of registered students daily. 
DELIMITER //
CREATE EVENT daily_report
ON SCHEDULE EVERY 2 DAY
STARTS '2023-03-07 00:00:00'
DO
BEGIN
    SELECT COUNT(*) AS total_students
    FROM students;
END//
SHOW EVENTS; -- OR SHOW EVENTS LIKE 'daily_report'

-- ✔ Create a view that uses at least 3-4 base tables, prepare and demonstrate a query that uses the view to 
-- produce a logically arranged result set for analysis.
-- quering the view table created in session 1 called usa_students_details
SELECT student_fname, course_name
FROM usa_students_details
ORDER BY 1;

-- 5 ✔ Prepare an example query with group by and having to demonstrate how to extract data from your DB for analysis
-- USING WHERE, GROUP BY AND HAVING
SELECT payment_method, MAX(amount) as max_amount
FROM payments
WHERE payment_date BETWEEN '2020-01-01' AND '2022-12-31'
GROUP BY payment_method
HAVING MAX(amount) < 1200;
