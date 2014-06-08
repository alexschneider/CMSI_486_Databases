title: 'Initial Planning'
date: 2014-06-07 13:50:17
categories:
- pyORMatic
---
This will be my plan for pyORMatic, a python ORM project aimed at supporting as many free and open source database systems as physically possible.

My application structure will have 3 separate layers.

1. Database Class.
 * Handles connecting to the database and performs all the raw queries that are specific to that database. There will be one abstract database class that each individual database will extend. This will handle reading data from the database, placing data into the database, updating data, and deleting data. It will also handle describing the database schema and creating database schema, so the program can handle switching between databases with ease. Finally, it will handle creating all the table classes for the database.
2. Table Class
 * This will be more or less identical across all the different types of databases. This will handle creating an object for each individual row in the database (from here on out, known as a database_object). It will also handle keeping the database_objects in sync with the database, and schema changes for tables.
3. DatabaseObject class
 * This class will be dynamically created by the table class so that it matches the database schema exactly. The class will only support setting and retrieving variables. Any other database manipulation should be handled in the Table class.

In addition to the above, there will be one "Master" class that will handle retrieving the database's respective class and initializing it, along with handling transfers from one database to another.

At first, this will only have CRUD operations and data caching. If time permits, more advanced features will be added, such as relations (joins), transaction rollback, relations, and other potentially database specific features (and emulating them on the software side).
