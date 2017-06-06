--- 
layout: post 
title:  NoSQL Distilled by Pramod J. Sadalage and Martin Fowler
tags:
- nosql
- scientific-computing
---
For those of us in the bioinformatics and genomics space, the advent of NoSQL databases offer multiple opportunities for storing "Big Data".  However, many of us are still grappling with the same set of questions:  when (if ever) does it make sense to switch over to NoSQL?  how much data does one need to justify a migration to NoSQL?  what types of genomic data sets and applications are ripe for NoSQL?  and, given the hundreds of NoSQL databases which now exist (see [nosql-database.org](http://nosql-database.org/)), which do you go with?

<div class="sidebar-left">
	<p>
		<b>Recommended Reading:</b>
	</p>
	<p>
		<ul>
			<li>NoSQL Distilled: A Brief Guide to the Emerging World of Polyglot Persistence.  By Pramod J. Sadalage, Martin Fowler.</li>
		<br/>
		<small>
		[<a href="http://goo.gl/M8ctmq">Amazon.com</a>]
		[<a href="http://martinfowler.com/nosql.html">Author web site</a>]
		[<a href="http://martinfowler.com/articles/nosql-intro">NoSQL Info Deck</a>]
		</small>
		</ul>
	</p>
</div>

None of these questions are easy, but if you are looking for a starting point to answering these questions on your own, I highly recommend [NoSQL:  Distilled](http://www.amazon.com/NoSQL-Distilled-Emerging-Polyglot-Persistence/dp/0321826620), by Pramod J. Sadalage and Martin Fowler.  [Martin Fowler](http://martinfowler.com/) is the author of several well-known computer software books, including a co-author of one of my favorites:  [Refactoring: Improving the Design of Existing Code](http://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672).  

At just 192 pages, *NoSQL:  Distilled* provides a concise, and highly readable overview of the new world of NoSQL.  The book is high level, and does not provide a detailed tutorial on any one NoSQL database.  Rather, it describes the pros and cons of NoSQL (along with the pros and cons of relational databases), describes the main types of NoSQL databases, and provides general advice on selecting a database, evolving software systems and creating application schemas.

Here are a few of the highlights I found most useful:

* we are entering a new world of [polyglot persistence](http://martinfowler.com/bliki/PolyglotPersistence.html), meaning that a single enterprise, or even a single application may need multiple types of database technologies, from relational to NoSQL.

* relational databases are really quite amazing.  We take them for granted now, but the authors remind us that relational database can have huge advantages, including simplicity, a standard query language, transaction support, and scalable replication.  As the authors conclude, "we realize that there are many cases, indeed the majority of cases, where you are better off sticking with the default [relational] option."

* the major downside of relational databases is that they are not designed to run on commodity clusters.  If you have enough data that it doesn't all fit on a single machine, NoSQL may be the way to go.

* NoSQL databases are not truly schemaless.  They simply shift the schema to the application code.  This can be great and fraught with difficulties at the same time.  Great because it simplifies application development.  A real problem if multiple applications access the same data store, and you need to evolve a shared schema.

* Best advice:  wrap your data store with a web service.  This enables you to evolve the data store as needed, even swapping in a NoSQL database for a relational one.

Unfortunately, *NoSQL Distilled* never gives any hard numbers on data size or performance metrics.  Without such data, it can be hard to make the ultimate leap to NoSQL.  Nonetheless, it is an extremely good book, and will get you on your way.




          
