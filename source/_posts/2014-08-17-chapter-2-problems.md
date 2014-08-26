title: Chapter 2 Problems
date: 2014-08-17 13:27:13
categories:
 - Exercises
---
These are selected problems from chapter two of the textbook that I'm using

<!-- more -->

2.12. Think of different users for the database shown in Figure 1.2. What types of applications would each user need? To which user category would each belong, and what type of interface would each need?

* Some of the different users could include students, professors, advisors, and administrators.
* Student view:
 * View grades
 * View classes
 * Register for classes
* Professor view:
 * View/set grades for all students in class
 * Set pre-requisites for class
 * Add or remove class
* Administrator view:
 * View all student grades
 * View student grades by professor/class
 * Add or remove student to/from class

2.14. If you were designing a Web-based system to make airline reservations and sell airline tickets, which DBMS architecture would you chose from Section 2.5? Why? Why would the other architectures not be a good choice?

I would probably use a three tier architecture. The reason being that airline tickets, by their nature, are very decentralized, and there's the possibility of needing to access or create the reservations and tickets from anywhere in the world by a large amount of audiences (such as the gate agents, the consumers, administrators at all levels, etc). Each audience requires a different view relating to the information that is shown to them, so the only way to show such a versatile view is by using the three tiered architecture. A two tiered architecture would require specialized applications for every view and would not translate well to the needs of the airliners.

2.15. Consider Figure 2.1. In addition to constraints relating the values of columns in one table to columns in another table, there are also constraints that impose restrictions on values in a column or a combination of columns within a table. One such constraint dictates that a column or a group of columns must be unique across all rows in the table. For example, in the STUDENT table, the Student_number column must be unique (to prevent two different students from having the same Student_number ). Identify the column or the group of columns in the other tables that must be unique across all rows in the table.

* Course:
 * Course_number
* Prerequisite:
  * Course_number and Prerequisite_number
* Section:
 * Section_identifier
* Grade_report:
 * Student_number and Section_identifier
