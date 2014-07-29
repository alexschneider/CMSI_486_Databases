title: Week Eight
date: 2014-07-21 22:13:15
categories:
 - Weekly Updates
---
I'm still down to the wire on this post, but at least I have more meaningful stuff to say. This week, as an overview, I managed to complete the MongoDB requriements early - last Tuesday, and spend all weekend working on pyORMatic (which, I've learned, doesn't have a link on the page. Let's [fix](https://github.com/alexschneider/pyORMatic) that). I've also added a link to the pyORMatic page.

I spent a good deal of time planning how I wanted to take my new ORM, and I think I've got a solid direction. Here are some of my considerations:

* I want to be able to store RICH objects
 * Unsurprisingly, Python has a [way to do it](https://docs.python.org/3.4/library/pickle.html)
 * To facilitate storing and retrieving data, I am going to have a custom object type that is similar to a dictionary (users of my ORM can treat it like one). It also supports attribute style accessors.
* I want to be able to quickly and easily switch between databases
 * As such, storing data in a human readable/queryable format is secondary. This means that all queries will have to be done through the ORM. Storage will be done in such a way that makes as much sense as possible (i.e. JSON format in Postgres, JSON as flat files, Blobs in MySQL), but as the data is binary encoded from pickling, this is secondary.
* The ORM should be simple - it supports "putting" an object, "getting" an object, "modifying" an object, and "deleting" an object. Anything else must be handled by user of the ORM.

Performance:

* I will let MySQL/Postgres/Mongo handle performance in their own way, doing my best to optimize queries to match the database's best case uses within my constraints.
* For flat files, I toyed with implementing sort of a B-Tree system, using binary search trees, or using indexes. My goal was to avoid overwriting the entire file after each database write, instead preferring to either append to the file or update only the line necessary. I ended up deciding (mostly out of laziness) to just overwrite the entire file and handle searching internally.
 * Thankfully, Python has many methods that make sorting and searching easier. Due to the old adage: "If I didn't write it, it occurs in asymptotically θ(1) time," all my code occurs in constant time!
 * On a more serious note, I was worried of becoming victim to [premature optimization](http://c2.com/cgi/wiki?PrematureOptimization). I decided to get the code working first, and go back for optimization afterward.

R.E. Mongo - this is also going well. I'm still at 100% completion on homework and tests. The performance considerations were very interesting to me, and had a pretty significant impact on how I decided to construct the database. I toyed with the idea of using indexes, and I still may, but managing indexes is very complicated, especially considering the number one consideration that I have for my database - rich data storage. Because pickling is storing binary data, it is difficult to organize data in a certain way. I'll keep doing research to see if it's at all possible though.
