title: Week Seven
date: 2014-07-14 08:09:25
categories:
 - Weekly Updates
---
Thus ends week three of the Mongo course. I STILL haven't had time to do much else, but in a couple of weeks I'm leaving on a trip where my internet access will be limited. I'm planning on spending a lot of time with the textbook and catching with pyORMatic then. I'll try to make more advances over the coming weeks, as they ought to be less hectic than the last couple of weeks.

This week in Mongo was about Schema design. More specifically, about how Schemaless design is "great." I've ranted a little in last week's post about this, but here's some more:

* It is nice to have a rich document design that can have many layers. This reduces the number of documents/tables needed to store related information. As such, One-One and One-Many relations are modeled quite easily in Mongo, assuming the data being stored is only pertinent to the parent document.  
* However, having such a rich document design has drawbacks, since it makes it difficult to have normalized data - that is, data that isn't repeated or replicated. Ideally, if something needed changing, one would only need to change it in one location.
* Furthermore, relations between tables have to be performed inside the programming language, rather than inside the database. There may be a way that I haven't learned yet to do relations within Mongo, but what I have learned just feels very clunky.

It felt like there were several workarounds that were needed to accurately model the relations. In the Mongo videos, the examples that they gave amounted to: "You would never actually need to do this with correct schema design", or "We don't need to store this data because it would contradict with our schema design".

For the homework this week, I did write a couple of one liners in python that were pretty awesome. A little bit of an aside: Functional constructs in langauges are amazing. They allow code to be incredibly short and once one understands them, can pack a ton of power into a single line of code.
