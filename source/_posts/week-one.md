title: Week One
categories:
 - Weekly Updates
---
## Introduction

This is the beginnings of my blog for the LMU CMSI 486 Databases independent study class, taught by Professor Mike Megally. As a part of the class, I will blog about my weekly progress and include updates on things that I have read, programs that I have written, and other things that may come up over the course of the summer.
<!-- more -->
Let me start by describing what a database is. According to the textbook I chose for this summer, [Fundamentals of Database Systems, 6th Edition](http://www.pearsonhighered.com/educator/product/Fundamentals-of-Database-Systems/9780136086208.page):

{% blockquote Elmasri & Navathe, Fundamentals of Database Systems %}
A database is a collection of related data. By data, we mean known facts that can be recorded and have implicit meaning.
{% endblockquote %}

So by that metric, anything that contains information or attributes about something is a database. Since this is a computer science class, I will focus primarily on the databases that are specifically designed for being used in programs. The aforementioned book laid out these properties for those types of databases:

{% blockquote Elmasri & Navathe, Fundamentals of Database Systems %}
* A database represents some aspect of the real world, sometimes called the miniworld or the universe of discourse (UoD). Changes to the miniworld are reflected in the database.
* A database is a logically coherent collection of data with some inherent meaning. A random assortment of data cannot correctly be referred to as a database.
* A database is designed, built, and populated with data for a specific purpose. It has an intended group of users and some preconceived applications in which these users are interested.
{% endblockquote %}

***

## Objectives

Since this is an independent study class, I have the luxury of choosing my own direction to a certain extent. I have, therefore, set these objectives for myself:

* Determine why traditional databases are important and what use do they serve me as a programmer.
* Different types of databases **(Chapters 2-3)**
 - Why are relational databases king? What are some alternative technologies that are up and coming or that relational databases overtook and what advantages and disadvantages do they have? **(Chapter 11)**
 - Design of databases: How are they structured under the hood? What decisions went into their design? **(Chapters 16-18)**
* Technical details about databases
 - How do they handle concurrent writes and duplicate writes? Why is this a problem? Should this be handled on the program side or the database side? **(Chapter 22)**
 - Advanced features of SQL (and other technologies) that go beyond the typical CRUD like triggers, assertions, etc. **(Chapter 5)**
 - Programming for databases **(Chapter 13)**
 - Optimizing databases: **(Chapters 19-20)**
  - Is it better to sort/join/etc within the database queries or within the program itself?
  - How to construct queries to be the most optimized.
  - Database schema optimization/normalization/denormalization **(Chapter 15)**
 - Transactions **(Chapter 21)**
* Database security from a programmer's perspective and from an administrator's perspective **(Chapter 24)**
* How to properly administer a database. **(Chapter 23)**
* Distributed databases: How do they work and what are they used for? **(Chapter 25)**
 - [PrestoDB](http://prestodb.io/)
* Theoretical stuff
 - Conceptual database and schema design **(Chapters 7-10)**
 - Relational algebra and calculus **(Chapter 6)**
 - Theoretical databases like Google's [F1](http://research.google.com/pubs/pub41344.html),

This is by no means an exhaustive list of things that I want to learn this semester, but I feel that it is a good start. I reserve the right to add or subtract things from the list as I learn more and more and progress through the course.

***

## Technologies

Here's a list of all the database technologies I know about and would like to learn more about. More will be added to the list as the summer goes on.

* SQL
 - MySQL (MariaDB)
 - Postgres
 - SQLite
 - MS-SQL
 - Oracle
 - H2
* NoSQL
 - MongoDB
* Key Value Stores
 - Redis
 - Memcached
* Flat Files

***

## Portfolio/Product

As a part of this course, I will produce the following (subject to change):

* A weekly blog post detailing my studies over the period, websites/academic papers that I found interesting, and summarizing the code or papers that I've written (Posted every Sunday).
* A comprehensive project that utilizes several of the aforementioned technologies.
* A substantial amount of problems from the textbook, to be published on this blog or on github.
* A compiled overview of what I've done over the course of the summer (most likely overwhelmingly copied and pasted from the blog posts that I've made)
