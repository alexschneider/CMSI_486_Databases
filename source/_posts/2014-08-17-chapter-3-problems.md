title: Chapter 3 Problems
date: 2014-08-17 13:54:02
categories:
 - Exercises
---
These are selected problems from chapter three of the textbook that I'm using

<!-- more -->

3.11. Suppose that each of the following Update operations is applied directly to the database state shown in Figure 3.6. Discuss all integrity constraints violated by each operation, if any, and the different ways of enforcing these constraints.
a. Insert <'Robert', 'F', 'Scott', '943775543', '1972-06-21', '2365 Newcastle Rd, Bellaire, TX', M, 58000, '888665555', 1> into EMPLOYEE .
b. Insert <'ProductA', 4, 'Bellaire', 2> into PROJECT .
c. Insert <'Production', 4, '943775543', '2007-10-01'> into DEPARTMENT .
d. Insert <'677678989', NULL , '40.0'> into WORKS_ON .
e. Insert <'453453453', 'John', 'M', '1990-12-12', 'spouse'> into DEPENDENT .
f. Delete the WORKS_ON tuples with Essn = '333445555'.
g. Delete the EMPLOYEE tuple with Ssn = '987654321'.
h. Delete the PROJECT tuple with Pname = 'ProductX'.
i. Modify the Mgr_ssn and Mgr_start_date of the DEPARTMENT tuple with Dnumber = 5 to '123456789' and '2007-10-01', respectively.
j. Modify the Super_ssn attribute of the EMPLOYEE tuple with Ssn = '999887777' to '943775543'.
k. Modify the Hours attribute of the WORKS_ON tuple with Essn = '999887777' and Pno = 10 to '5.0'.

a. No constraints violated
b. Department doesn't exist - a referential integrity constraint would be violated.
c. Department number is a duplicate of the Administration department. The primary key integrity would be violated.
d. Project number cannot be null - it violates the entity integrity constraint.
e. No constraints violated (though an age gap of 18 years between the couple is a bit concerning).
f. No constraints violated.
g. Must have a cascading delete for WORKS_ON and DEPENDENT
h. Must have a cascading delete for WORKS_ON
i. No constraints violated
j. SSN doesn't exist - referential integrity constraint would be violated.
k. No constraints violated

3.12. Consider the AIRLINE relational database schema shown in Figure 3.8, which describes a database for airline flight information. Each FLIGHT is identified by a Flight_number , and consists of one or more FLIGHT_LEG s with Leg_number s 1, 2, 3, and so on. Each FLIGHT_LEG has scheduled arrival and departure times, airports, and one or more LEG_INSTANCEs-one for each Date on which the flight travels. FARE s are kept for each FLIGHT . For each FLIGHT_LEG instance, SEAT_RESERVATION s are kept, as are the AIRPLANE used on the leg and the actual arrival and departure times and airports. An AIRPLANE is identified by an Airplane_id and is of a particular AIRPLANE_TYPE . CAN_LAND relates AIRPLANE_TYPEs to the AIRPORTs at which they can land. An AIRPORT is identified by an Airport_code. Consider an update for the AIRLINE database to enter a reservation on a particular flight or flight leg on a given date.
a. Give the operations for this update.
b. What types of constraints would you expect to check?
c. Which of these constraints are key, entity integrity, and referential
integrity constraints, and which are not?
d. Specify all the referential integrity constraints that hold on the schema
shown in Figure 3.8.

a. The operations needed would be to add the following
 * Flight
 * Flight_leg
 * Leg_instance
 * Fare
b. The constraints to be checked would be the following
 * For flight:
  * Flight number is unique
  * Weekdays is between 0 and 6 or 1 and 7, depending
 * For Flight_leg
  * Flight_number matches up with something in Flight
  * Leg_number is unique
  * Departure_airport_code and Arrival_airport_code are valid and in the airport table.
 * For Leg_instance
  * Flight number and leg_number match up with their respective tables
  * Airplane_id exists in the Airplane table
  * Airplane_type from airplane_id matches up with the airport code in the arrival for "can land".
 * For Fare:
  * Flight_number matches up with a valid number
  * Fare_code is unique
  * Amount is non-negative/non-zero

3.13. Consider the relation CLASS ( Course# , Univ_Section# , Instructor_name , Semester , Building_code , Room# , Time_period , Weekdays , Credit_hours ). This represents classes taught in a university, with unique Univ_section# s. Identify what you think should be various candidate keys, and write in your own words the conditions or assumptions under which each candidate key would be valid.

Course# has to exist in another table, Univ_Section# has to exist in another table, Instructor_name must not be null, Semester must be one of 3 (4 if on the quarter system), Building code must exist on campus, and Room# must exist in teh building. Time_period, Weekdays, and Credit_hours must be valid.

3.14. Consider the following six relations for an order-processing database application in a company:
```
CUSTOMER(Cust#, Cname, City)
ORDER(Order#, Odate, Cust#, Ord_amt)
ORDER_ITEM(Order#, Item#, Qty)
ITEM(Item#, Unit_price)
SHIPMENT(Order#, Warehouse#, Ship_date)
WAREHOUSE(Warehouse#, City)
```
Here, Ord_amt refers to total dollar amount of an order; Odate is the date the order was placed; and Ship_date is the date an order (or part of an order) is shipped from the warehouse. Assume that an order can be shipped from several warehouses. Specify the foreign keys for this schema, stating any assumptions you make. What other constraints can you think of for this database?

The foreign keys are Cust# in ORDER, Order# and Item# in ORDER_ITEM, and Order# and Warehouse# in SHIPMENT. Constraints may include keeping all the keys "NOT NULL", and ensuring validity of the item types.

3.15. Consider the following relations for a database that keeps track of business trips of salespersons in a sales office:
```
SALESPERSON(Ssn, Name, Start_year, Dept_no)
TRIP(Ssn, From_city, To_city, Departure_date, Return_date, Trip_id)
EXPENSE(Trip_id, Account#, Amount)
```
A trip can be charged to one or more accounts. Specify the foreign keys for this schema, stating any assumptions you make.

 The foreign keys would be Ssn from TRIP and Trip_id from EXPENSE, assuming that each trip refers to only one employee.

 3.16. Consider the following relations for a database that keeps track of student enrollment in courses and the books adopted for each course:
 ```
STUDENT(Ssn, Name, Major, Bdate)
COURSE(Course#, Cname, Dept)
ENROLL(Ssn, Course#, Quarter, Grade)
BOOK_ADOPTION(Course#, Quarter, Book_isbn)
TEXT(Book_isbn, Book_title, Publisher, Author)
```
Specify the foreign keys for this schema, stating any assumptions you make.

The foreign keys would be Ssn and Course# from ENROLL and Course# and Book_isbn from BOOK_ADOPTION.

3.18. Database design often involves decisions about the storage of attributes. For example, a Social Security number can be stored as one attribute or split into three attributes (one for each of the three hyphen-delineated groups of numbers in a Social Security number\u2014XXX-XX-XXXX). However, Social Security numbers are usually represented as just one attribute. The decision is based on how the database will be used. This exercise asks you to think about specific situations where dividing the SSN is useful.

Social security numbers are categorized by location - beginnning in the northeast and moving to the southwest. Though this isn't 100% accurate (especially in recent years, the numbers tend to be more random), it still may be useful if one wants to separate people by their geographic location.

3.20. Recent changes in privacy laws have disallowed organizations from using Social Security numbers to identify individuals unless certain restrictions are satisfied. As a result, most U.S. universities cannot use SSNs as primary keys (except for financial data). In practice, Student_id , a unique identifier assigned to every student, is likely to be used as the primary key rather than SSN since Student_id can be used throughout the system.
a. Some database designers are reluctant to use generated keys (also known as surrogate keys) for primary keys (such as Student_id ) because they are artificial. Can you propose any natural choices of keys that can be used to identify the student record in a UNIVERSITY database?
b. Suppose that you are able to guarantee uniqueness of a natural key that includes last name. Are you guaranteed that the last name will not change during the lifetime of the database? If last name can change, what solutions can you propose for creating a primary key that still includes last name but remains unique?
c. What are the advantages and disadvantages of using generated (surrogate) keys?

a. A hybrid key consisting of a student's birth date, their first and last name, and their hometown is most likely unique, though there is the posibility for some collisions.
b. Last names are not guaranteed to remain consistent. However, they are not guarenteed to be unique either, so the uniqueness must come from some other part of the primary key. Since prior to the change the key was unique, the possibility of it remaining unique after the change is high (depending on the factors used to generate the key, and assuming that they are not arbitrary).
c. Some advantages:
 * Uniqueness can be guaranteed with a generated key
 * Generated primary keys are easy to link multiple tables together since they are easily understood by computer programs, and they can meet whatever specs the system calls for.
Some disadvantages
 * Arbitrary data means that it can be difficult to replace corrupt data
 * Similar issues with transferring details to a new system, the generated primary key may cause issues with the data.
