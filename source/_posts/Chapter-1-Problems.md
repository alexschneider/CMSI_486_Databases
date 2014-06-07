title: 'Chapter 1 Problems'
date: 2014-06-06 20:07:39
categories:
 - Exercises
---
These are selected problems from chapter one of the textbook that I'm using

<!-- more -->

1.8. Identify some informal queries and update operations you would expect to apply to the database shown in Figure 1.2
* Select all students whose major is computer science
* Add a new course
* Change course's instructor
* Select all students who have a GPA of above 3.5
* Show available course for a student to take based on prerequisites

1.9. What is the difference between controlled and uncontrolled redundancy? Illustrate with examples.
* Redundancy involves storing the same information in more than one place, often to improve performance of queries
* Controlled redundancy is when the data is kept in sync across all of its locations. Often databases provide mechanisms towards this goal.
* Uncontrolled redundancy occurs when data is out of sync, two different records referring to the same thing have different values.
* Obviously, controlled redundancy is more desirable.

1.10. Specify all the relationships among the records of the database shown in Figure 1.2.
* STUDENT is related to:
 - GRADE_REPORT
* COURSE is related to:
 - SECTION
 - PREREQUISITE
* SECTION is related to:
 - COURSE
 - GRADE_REPORT
* GRADE_REPORT is related to:
 - STUDENT
 - SECTION
* PREREQUISITE is related to:
 - COURSE

1.11. Give some additional views that may be needed by other user groups for the database shown in Figure 1.2.
* Transcript (Students, courses, and grades)
* Course assignment (Students, courses, sections, and prerequisite)
* Change course listing (Section, course name)

1.12. Cite some examples of integrity constraints that you think can apply to the database shown in Figure 1.2.
* Grade can only be ABCD or F
* Students can't take more than a certain amount of classes or two of the same classes in the same semester and year
* A course can't depend on itself as a prerequisite

1.13. Give examples of systems in which it may make sense to use traditional file processing instead of a database approach.
* Limited resources - traditional file processing doesn't require much storage space or processor time.
* Extremely specific applications - Traditional file processing is easier to read and write to for a programmer and may not need the overhead of a database if only one user is going to use it at a time.
* Data that doesn't fit well in a database - Some data is too big for a database to handle reliably, or is a specific specification that makes it unsuitable for databases.

1.14. Consider Figure 1.2.
**a.** If the name of the 'CS' (Computer Science) Department changes to 'CSSE' (Computer Science and Software Engineering) Department and the corresponding prefix for the course number also changes, identify the columns in the database that would need to be updated
 * STUDENT/Major
 * COURSE/Course_number and COURSE/Department
 * PREREQUISITE/Course_number and PREREQUISITE/Prerequisite_number

**b.** Can you restructure the columns in the COURSE, SECTION, and PREREQUISITE tables sot hat only one column will need to be updated?
 * Add a new table called DEPARTMENT with two columns, Department_name and Department_identifier.
 * Replace STUDENT/Major and COURSE/Department with the Department_identifier
 * Ensure that the Course_numbers are unique, and remove the letter prefix from them. Add a new column in all the tables that have the Course_numbers column called Course_department, fill in with Department_identifier
