-- Create database
CREATE DATABASE Employe;

-- Use the database
USE EmployeeDB;

-- Create Employee Details table
CREATE TABLE Details (
    Employee_Id VARCHAR(100),
    Employee_name VARCHAR(100),
    dateofBirth DATE,
    DateOfjoining DATE,
    Salary INT,
    Bonus INT,
    City VARCHAR(100),
    Address VARCHAR(100),
    Department VARCHAR(100),
    Employee_mail_id VARCHAR(100),
    Employee_status VARCHAR(100),
    Timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    Phone_number VARCHAR(10)
);

-- Display the table structure
DESC Details;

-- Insert values into the table
INSERT INTO employe (s_no, employee_id, employee_name, date_of_birth, date_of_joining, salary, bonus, city, address, department, emp_mail_id, emp_status) VALUES
(1, 101, 'abi', '1990-05-15', '2015-06-20', 60000, 5000, 'Coimbatore', '123 Main St', 'HR', 'abi@gmail.com', 'A'),
(2, 102, 'mani', '1988-09-22', '2016-07-10', 65000, 5500, 'dindugul', '456 Elm St', 'Finance', 'mani@gmail.com', 'A'),
(3, 103, 'asif', '1992-11-05', '2017-03-15', 62000, 5200, 'udumalai', '789 Oak St', 'IT', 'asif@gmail.com', 'A'),
(4, 104, 'dharani', '1995-02-18', '2018-05-25', 58000, 4800, 'theni', '321 Pine St', 'Marketing', 'dharani@gmail.com', 'A'),
(5, 105, 'preethi', '1985-07-30', '2014-09-12', 70000, 6000, 'neiveli', '654 Cedar St', 'Sales', 'preethi@gmail.com', 'A'),
(6, 106, 'deepika', '1993-12-10', '2019-11-30', 59000, 4900, 'pollachi', '987 Birch St', 'HR', 'deepika@gmail.com', 'A'),
(7, 107, 'sree', '1989-04-25', '2013-08-18', 67000, 5700, 'coimbatore', '159 Maple St', 'Finance', 'sree@.gmailcom', 'IA'),
(8, 108, 'abish', '1991-06-08', '2020-01-05', 61000, 5100, 'erode', '753 Walnut St', 'IT', 'abish@gmail.com', 'A'),
(9, 109, 'pravin', '1986-03-14', '2012-04-22', 72000, 6200, 'viruthunagar', '852 Spruce St', 'Marketing', 'pravin@gmail.com', 'IA'),
(10, 110, 'dhanush', '1994-08-19', '2021-07-14', 56000, 4600, 'pollachi', '963 Fir St', 'Sales', 'dhanush@gmail.com', 'A');

-- Change column name from Employee_name to First_name
ALTER TABLE Details
CHANGE COLUMN Employee_name First_name VARCHAR(100);

-- Add new column Age
ALTER TABLE Details
ADD COLUMN Age INT;

-- Update Age based on date of birth
UPDATE Details
SET Age = TIMESTAMPDIFF(YEAR, dateofBirth, CURDATE());

-- Drop Employee_status column
ALTER TABLE Details
DROP COLUMN Employee_status;

-- Delete a record
DELETE FROM Details WHERE Employee_Id = 'ds006';

-- Queries:

-- Display names ending with 'a'
SELECT * FROM Details WHERE First_name LIKE '%a';

-- Employees with salary more than 70,000
SELECT * FROM Details WHERE Salary > 70000;

-- Employees from Chennai
SELECT * FROM Details WHERE City = 'Chennai';

-- Employees aged 19 in the Finance department
SELECT * FROM Details WHERE Age = 19 AND Department = 'Finance';

-- Count of employees with salary more than 90,000
SELECT COUNT(*) FROM Details WHERE Salary > 90000;

-- Average age in Finance department
SELECT AVG(Age) FROM Details WHERE Department = 'Finance';

-- Maximum and Minimum Salary
SELECT MAX(Salary) AS Highest_Salary FROM Details;
SELECT MIN(Salary) AS Lowest_Salary FROM Details;

-- Employees whose name starts with 'A'
SELECT * FROM Details WHERE First_name LIKE 'A%';

-- Employees with 'A' in the middle of their name and salary between 85,000 and 90,000
SELECT * FROM Details WHERE First_name LIKE '%a%' AND Salary BETWEEN 85000 AND 90000;

-- Truncate the table (Deletes all records but keeps structure)
TRUNCATE TABLE Details;

