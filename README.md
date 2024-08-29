school-district-performance-analysis/
│
├── README.md
└── sql_queries/
    ├── student_insights_1.sql
    ├── student_insights_2.sql
    ├── teacher_analysis_1.sql
    ├── teacher_analysis_2.sql
    ├── class_performance_1.sql
    ├── class_performance_2.sql
    ├── enrolment_trends_1.sql
    ├── enrolment_trends_2.sql



# school-district-sql-project
SQL Project to analyze student performance and educational outcomes for a school district.

# School District Performance Analysis

## Overview

This project contains a series of SQL queries designed to analyze student performance, teacher efficiency, class performance, and enrollment trends within a school district. The goal is to extract actionable insights to improve educational outcomes.

## Database Structure

The database includes the following tables:

1. **Students**
2. **Teachers**
3. **Classes**
4. **Enrolments**
5. **Grades**

## SQL Tasks and Queries

### Task 1: Student Insights




1. **Number of Students Enrolled in Each Grade Level**

   ```sql
   -- Get the number of students enrolled in each grade level.
   -- This report helps in understanding the distribution of students across different grades.

   SELECT
       grade_level,
       COUNT(student_id) AS number_of_students
   FROM
       Students
   GROUP BY
       grade_level;



2. **Top 5 Students with the Highest Average Grades**

  
-- Find the top 5 students with the highest average grades.
-- This report helps in identifying the top-performing students based on their average grades.

SELECT
    student_id,
    AVG(grade) AS average_grade
FROM
    Grades
GROUP BY
    student_id
ORDER BY
    average_grade DESC
LIMIT 5;


## Task 2: Teacher Analysis

### 1. Average Number of Students per Class for Each Teacher

This report helps in evaluating the teacher's class sizes and teaching load.

### Task 2: Teacher Analysis

#### 2. Teacher with the Highest Number of Classes Taught

This report helps in understanding which teacher has the highest teaching load.

```sql
-- Identify the teacher with the highest number of classes taught.

SELECT
    teacher_id,
    COUNT(class_id) AS number_of_classes
FROM
    Classes
GROUP BY
    teacher_id
ORDER BY
    number_of_classes DESC
LIMIT 1;

-- Calculate the average number of students per class for each teacher.

SELECT
    teacher_id,
    AVG(student_count) AS average_students_per_class
FROM
(
    SELECT
        t.teacher_id,
        COUNT(e.student_id) AS student_count
    FROM
        Teachers t
        JOIN Classes c ON t.teacher_id = c.teacher_id
        JOIN Enrolments e ON c.class_id = e.class_id
    GROUP BY
        t.teacher_id, c.class_id
) AS class_data
GROUP BY
    teacher_id;




### Task 2: Teacher Analysis

#### 2. Teacher with the Highest Number of Classes Taught

This report helps in understanding which teacher has the highest teaching load.

```sql
-- Identify the teacher with the highest number of classes taught.

SELECT
    teacher_id,
    COUNT(class_id) AS number_of_classes
FROM
    Classes
GROUP BY
    teacher_id
ORDER BY
    number_of_classes DESC
LIMIT 1;




