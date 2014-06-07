title: 'Week Two'
date: 2014-06-06 09:52:39
categories:
 - Weekly Updates
---

So the first week I didn't really do much for the class. I think I've decided to not do the MongoDB course in effort to try to learn on my own. I figure that if that doesn't work, I can always pick up the course when the Python one comes around, on June 24th. I've also spent a great deal of time trying to come up with a project that would not only advance my own skills, but also benefit others. So far, I've been unable to determine one, but I've decided that an interesting way to begin the project would be to write my own custom ORM.
<!-- more -->
To kick start the discussion, here's a quote from wikipedia on what an ORM is:

{% blockquote Wikipedia http://en.wikipedia.org/wiki/Object-relational_mapping Object Relational Mapping %}
Object-relational mapping in computer software is a programming technique for converting data between incompatible type systems in object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language.
{% endblockquote %}

I had some experience with writing an ORM when I was doing Project 21 last semester, but it was very basic, rudimentary, and targeted towards Postgres and the specific app that we were writing. Ideally, the ORM that I write will be database agnostic - that is, one can pick any type of database to store their data - and be highly generalized, so that any application can easily use it. My main grievance is that there is not often one single interface that allows switching between a large number of databases. Since I haven't really used any ORMs before, I think this will be a great way to understand how databases interact with the application layer. Once I'm done, I can compare it to established ORMs, and see how the decisions I made affected the overall performance and stability. Finally, I will do it in Python. I haven't really created a massive project from scratch with Python, and thus, my understanding of how classes work in Python is somewhat limited. My goal will be to use as many language specific features as possible for Python.

A couple of decisions that I will need to make:

* Caching - automatic or manual?
* How much to rely on SQL or language specific features beyond the simple CRUD?
* How much functionality to provide to users? How much "magic" should be going on behind the scenes?
* How to reconcile the differences between the databases so that the user shouldn't have to change their code to change databases?
* What data types to support - different databases support different types. How should I reconcile the differences?
* ORMs make sense for relational databases, how much sense would they make for non-relational databases?

I'll probably create a new page to track my progress with this. Link TBD.

Finally, I'll also have a separate page for the book problems. [Exercises](/CMSI_486_Databases/categories/Exercises/)
