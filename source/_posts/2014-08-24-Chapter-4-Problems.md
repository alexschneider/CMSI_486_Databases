title: Chapter 4 Problems
date: 2014-08-24 14:09:38
tags:
---
Notes:
* SQL is a standard language that all implementations must follow.
* SQL has several data types - numeric, character/string, bit-string, boolean, and date
* Constraints can further limit the data input in a table, such as verifying the size of the data, setting default values, or preventing NULLs from occurring
 * Constraints can be named
 * Constraints help enforce integrity of data
* SQL has a retrieval statement called "SELECT"
 * Usually paired with "FROM" and "WHERE"
 * Where clause limits the rows returned from the select statement
* SQL has a pattern matching statment called "LIKE"

<!-- more -->

4.5. Consider the database shown in Figure 1.2, whose schema is shown in Figure 2.1. What are the referential integrity constraints that should hold on then schema? Write appropriate SQL DDL statements to define the database

Constraints:
 * Student_number PRIMARY
 * Course_number PRIMARY
 * Course_name UNIQUE
 * Section_identifier PRIMARY
 * Grade IN ("A", "B", "C", "D", "F")
4.6. Repeat Exercise 4.5, but use the AIRLINE database schema of Figure 3.8.

Constraints:
 * Airport_code PRIMARY
 * Flight_number PRIMARY
 * Weekdays BETWEEN 0 AND 6
 * Leg_number PRIMARY
 * Airplane_type_name PRIMARY
 * Airplane_id PRIMARY

4.7. Consider the LIBRARY relational database schema shown in Figure 4.6. Choose the appropriate action (reject, cascade, set to NULL , set to default) for each referential integrity constraint, both for the deletion of a referenced tuple and for the update of a primary key attribute value in a referenced tuple. Justify your choices.

* Book_id - CASCADE - without a book_id, there'll be no book_author, no book copies, or book loans
* Name (publisher) - REJECT on update - once a book has been published, the publisher cannot change for pre-existing copies of a book. Set to NULL on delete - ensure that no denormalized data exists.
* Branch_id - CASCADE on update (there shouldn't be any updates really), REJECT on delete - books need to be manually moved
* Card_no - CASCADE on update (shouldn't be any updates), set to NULL on deletes

4.9. How can the key and foreign key constraints be enforced by the DBMS? Is the enforcement technique you suggest difficult to implement? Can the constraint checks be executed efficiently when updates are applied to the database?

Key and foreign key constraints can be enforced by the DBMS by using a metatable of them, and whenever a query (UPDATEs and DELETEs) that could possibly run up against the restrictions, query the meta-table to see if there is a constraint.

The technique would require an additional query to be run for all updates and deletes, which increases overhead, but is rather simple to implement.

4.10. Specify the following queries in SQL on the COMPANY relational database
schema shown in Figure 3.5. Show the result of each query if it is applied to the COMPANY database in Figure 3.6.
a. Retrieve the names of all employees in department 5 who work more than 10 hours per week on the ProductX project.
b. List the names of all employees who have a dependent with the same first name as themselves.

a.
```
SELECT e.Fname FROM EMPLOYEE e INNER JOIN WORKS_ON w INNER JOIN Project p ON e.Ssn = w.Essn, p.Pnumber=w.Pno WHERE w.Hours > 10  AND p.Pname='ProjectX'
```

Result:
```
John
Joyce
```
b.
```
SELECT e.Fname FROM EMPLOYEE e INNER JOIN DEPENDENT d ON e.Ssn = d.Essn WHERE d.Dependant_name=e.Fname
```

Result:
```
(no results)
```

4.11. Specify the updates of Exercise 3.11 using the SQL update commands.
a. `INSERT INTO EMPLOYEE VALUES (‘Robert’, ‘F’, ‘Scott’, ‘943775543’, ‘1972-06-21’, ‘2365 Newcastle Rd, Bellaire, TX’, M, 58000, ‘888665555’, 1)`
b. `INSERT INTO PROJECT VALUES ('ProductA', 4, 'Bellaire', 2)`
c. `INSERT INTO DEPARTMENT VALUES (‘Production’, 4, ‘943775543’, ‘2007-10-01’)`
d. `INSERT INTO WORKS_ON VALUES ('677678989', NULL, '40.0')`
e. `INSERT INTO DEPENDENT VALUES (‘453453453’, ‘John’, ‘M’, ‘1990-12-12’, ‘spouse’)`
f. `DELETE FROM WORKS_ON WHERE Essn='333445555'`
g. `DELETE FROM EMPLOYEE WHERE Ssn='987654321'`
h. `DELETE FROM PROJECT WHERE Pname='ProductX'`
i. `UPDATE DEPARTMENT SET Mgr_ssn='123456789', Mgr_start_date='2007-10-01' WHERE Dnumber=5`
j. `UPDATE EMPLOYEE SET Super_ssn='943775543' WHERE Ssn='999887777'`
k. `UPDATE WORKS_ON SET Hours='5.0' WHERE Essn='999887777' AND Pno=10`

4.12 Specify the following queries in SQL on the database schema of Figure 1.2.
a. Retrieve the names of all senior students majoring in ‘CS’ (computer science).
b. Retrieve the names of all courses taught by Professor King in 2007 and 2008.
c. For each section taught by Professor King, retrieve the course number, semester, year, and number of students who took the section.
d. Retrieve the name and transcript of each senior student (Class = 4) majoring in CS. A transcript includes course name, course number, credit hours, semester, year, and grade for each course completed by the student.

a. `SELECT Name FROM STUDENT WHERE Major='CS'`
b. `SELECT c.Course_name FROM COURSE c INNER JOIN SECTION s ON c.Course_number=s.Course_number WHERE s.Instructor='King' AND (YEAR=08 OR YEAR=09)`
c. `SELECT s.Course_number, s.Semester, s.Year, COUNT(g.Student_number) FROM GRADE_REPORT g INNER JOIN SECTION s ON g.Section_identifier=s.Section_identifier WHERE s.Instructor='King'`
d.
```
SELECT st.Name, c.Course_name, sec.Course_number, c.Credit_hours, sec.Semester, sec.Year, g.Grade
  FROM STUDENT st
  INNER JOIN GRADE_REPORT g ON st.Student_number=g.Student_number
  INNER JOIN SECTION sec ON sec.Section_identifier=g.Section_identifier
  INNER JOIN COURSE c ON sec.Course_number=c.Course_number
WHERE st.Class=4
```

4.13. Write SQL update statements to do the following on the database schema shown in Figure 1.2.
a. Insert a new student, <‘Johnson’, 25, 1, ‘Math’>, in the database.
b. Change the class of student ‘Smith’ to 2.
c. Insert a new course, <‘Knowledge Engineering’, ‘CS4390’, 3, ‘CS’>.
d. Delete the record for the student whose name is ‘Smith’ and whose stu-
dent number is 17.

a. `INSERT INTO STUDENT VALUES ('Johnson', 25, 1, 'MATH')`
b. `UPDATE STUDENT SET Class=2`
c. `INSERT INTO COURSE VALUES (‘Knowledge Engineering’, ‘CS4390’, 3, ‘CS’)`
d. `DELETE FROM STUDENT WHERE Student_number=17 AND Name='Smith'`

4.15. Consider the EMPLOYEE table’s constraint EMPSUPERFK as specified in
Figure 4.2 is changed to read as follows:
```
CONSTRAINT EMPSUPERFK
FOREIGN KEY ( Super_ssn ) REFERENCES EMPLOYEE ( Ssn )
ON DELETE CASCADE ON UPDATE CASCADE ,
```
Answer the following questions:
a. What happens when the following command is run on the database state shown in Figure 3.6?
```
DELETE EMPLOYEE WHERE Lname = ‘Borg’
```
b. Is it better to CASCADE or SET NULL in case of EMPSUPERFK constraint ON DELETE ?

a. The employee's boss will also be deleted.
b. It is probably better to SET NULL, since the employee can get a new boss and the employee being fired doesn't necessarily mean that their boss gets fired too.

4.16. Write SQL statements to create a table EMPLOYEE_BACKUP to back up the EMPLOYEE table shown in Figure 3.6.

```
INSERT INTO EMPLOYEE_BACKUP SELECT * FROM EMPLOYEE
```
