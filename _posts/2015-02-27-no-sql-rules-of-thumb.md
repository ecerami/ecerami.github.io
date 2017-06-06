--- 
layout: post 
title:  Rules of Thumb for Migrating to NoSQL
tags:
- nosql
- databases
---

As covered in [previous posts](http://biobits.org/nosql-distilled.html), it is difficult to determine if or when to migrate to a NoSQL database technology.

I have yet to find any concrete metrics on the matter.  And, have therefore started my own rules of thumb:

**Rule of Thumb 1:** If you are on the scale of a Google or Facebook, then you should definitely consider NoSQL.  For example, according to MongoDB, Facebook ingests [500 terabytes of new data a day](http://www.mongodb.com/big-data-explained).  Much of this is likely photos and videos, and it's not clear if this truly needs to be stored in a database versus a distributed file store, but you get the idea.  If you have anything approaching this scale, go with NoSQL.

**Rule of Thumb 2:**  You are probably not Google or Facebook.  Keep reading the remaining rules of thumb.

**Rule of Thumb 3:**  Many people, vendors, developers, etc. will try to convince you that you have "big data", that relational databases do not scale, and you must therefore adopt NoSQL.  Do not fall for this.  Rather, accept their advice with two large grains of salt:  1)  companies, such as MongoDB want to sell you something, and it's in their interest to have you use their product, even if you don't really need it;  and 2)  developers like to try new technologies;  nothing wrong with that, but just make sure that you don't end up refactoring an entire system, just because people want to try cool, new technologies.    

**Rule of Thumb 4:**  Segregate your data into bins, and figure out which bins truly need to be in a database.  This will obviously vary, depending on your data and applications.  

For example, consider "big genomic data".  The [Cancer Genomics Hub](https://cghub.ucsc.edu/index.html), currently hosted by U.C. Santa Cruz redistributes data for multiple cancer genomic projects, including the TCGA and CCLE.  According to the [latest stats](https://cghub.ucsc.edu/summary_stats.html), it currently hosts 2033.936 terabytes, or ~2 petabytes of data.  That is a lot of data, but nearly all of it is in the form of BAM files, which are  redistributed in their entirety and not (currently) stored in a database.  This will likely change in the future, and new database technologies will likely support BAM slicing, e.g. random access to specific genomic coordinates (for example, see [Google Genomics](https://cloud.google.com/genomics/)).  But, until then, consider if your primary data truly needs to be in a database versus a file store.  Then, consider the type and scale of secondary or derived data sets.  For example,  variant and fusion calls (derived from BAM files) are usually the most important data elements for biological and clinical interpretation, and they represent a tiny fraction of the primary data.

**Rule of Thumb 5:**  If all your data fits on one large hard drive, e.g. a single 1TB - 5TB hard drive, stick with a relational database.  The real benefit of NoSQL technology, such as MongoDB derives from the fact that you can more easily shard data across multiple machines.  If everything already fits on one machine, there is not much rationale for adopting NoSQL.  You are better off sticking with a relational database.  You already know how they work, you can happily do joins, and you can get back to building your application.  If you have no idea how much data you really have or expect to have in the future, continue on with the next rule.

**Rule of Thumb 6:**  When in doubt, benchmark the scale of your current and future data using *simulated data*.  To be concrete, create a sandbox application (relational or otherwise), load it with tons of simulated data, and determine how much storage this simulated data takes up on one machine.  For example, pick the data element that is most likely to grow over time, and then create simulated data at discrete levels, e.g. 10,000 objects, 100,000 objects, 1 million objects, etc.  Collect enough data points, and you can then estimate storage sizes required for future growth.  If future storage sizes have little chance of being stored on a single (large) machine, you are likely in NoSQL territory.  Otherwise, stick with a tried and true relational database, and get back to your application.

