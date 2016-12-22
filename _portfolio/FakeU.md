---
title: "FakeU"
header:
  <!-- image: assets/images/profile.jpg -->
  teaser: assets/images/fakeu1.JPG
---
University class database implemented in PostgreSQL.  

Data was supplied as .csv files, parsed in with Python and fed into PostgreSQL using [psycopg2](http://initd.org/psycopg/).  

[Full specs here](/assets/docs/Homework04.pdf)  

Queries:  
1. Calculate the percent of students that attempt 1 – 20 units of ABC or DEF
per quarter for every unit increment (e.g. 1, 2, 3,…).  
1. Calculate the average GPA for the students that take each number of units
from part a. Assume that the grades have standard grade points (A+ = 4.0,
A = 4.0, A- = 3.7, B+ = 3.3…).  
1. Find the easiest and hardest instructors based upon the grades of all the
students they have taught in their courses. Provide their name and the
average grade they assigned.  
1. Do the analysis again for each ABC 100 level course that is offered, which
instructor is the easiest/most difficult. For each course provide the
instructors name and the average grade they assigned.  
1. Find the list of courses that must have been offered in different summer
sessions as they have meeting conflicts. Only list the pair once, put the
course name/number string in alphabetically order of the pairs.  
1. What major performs the best/worst on average in ABC courses?  
1. What percent of students transfer into one of the ABC majors? What are
the top 5 majors that students transfer from into ABC, and what is the
percent of students from each of those majors?  

## Here's some code (for #4):
```sql
----MAX GPA
SELECT * 
FROM(
  (SELECT subject,course,instructor, weight / units AS gpa 
    FROM(
      SELECT subject,course,instructor, SUM(units) AS units, SUM(weight) AS weight 
      FROM (
        SELECT subject,course,instructor,units,points*units AS weight 
        FROM (course 
          NATURAL JOIN takes 
          NATURAL JOIN gradenumbers) 
        WHERE instructor IS NOT NULL AND subject = 'ABC' AND CAST(course AS INTEGER) >= 100 AND CAST(course AS INTEGER) < 200
        ORDER BY instructor) AS v1 
      GROUP BY subject,course,instructor) AS v2
    ORDER BY course,gpa) as v4

  NATURAL JOIN

  (SELECT subject,course,MAX(gpa) AS gpa
  FROM(
    SELECT subject,course,instructor, weight / units AS gpa 
    FROM(
      SELECT subject,course,instructor, SUM(units) AS units, SUM(weight) AS weight 
      FROM (
        SELECT subject,course,instructor,units,points*units AS weight 
        FROM (course 
          NATURAL JOIN takes 
          NATURAL JOIN gradenumbers) 
        WHERE instructor IS NOT NULL AND subject = 'ABC' AND CAST(course AS INTEGER) >= 100 AND CAST(course AS INTEGER) < 200
        ORDER BY instructor) AS v1 
      GROUP BY subject,course,instructor) AS v2
    ORDER BY course,gpa) as v3
  GROUP BY subject,course
  ORDER BY course) as v5)
```
Full source available on request.