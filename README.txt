NUTCH-MONGODB-INDEXER README

Compatible With:
   Nutch 1.3

For the latest information about Nutch, please visit the website at:

   http://nutch.apache.org

our the wiki, at:

   http://wiki.apache.org/nutch/

To get started using Nutch read Tutorial:

   http://wiki.apache.org/nutch/NutchTutorial

For the latest information about Mongodb, please visit the website at:

   http://www.mongodb.org/

our the wiki, at:

   http://www.mongodb.org/display/DOCS/Home

To get started using Mongodb and Java read these Tutorials

   http://www.mongodb.org/display/DOCS/Quickstart
   http://www.mongodb.org/display/DOCS/Java+Tutorial

Important Stuff

This patch was created to allow for the indexing of Nutch crawl data directly into Mongodb.  This is similar in nature to that of the SolrIndexer that comes with Nutch which let you index directly into Solr.  This provides a way directly index data into Mongodb coming directly from Nutch.    

This is just the code necessary to create the solution.  You must start by having the Nutch codebase and have it setup in your development environment (Eclipse) see http://wiki.apache.org/nutch/RunNutchInEclipse for how do this.  Once you are set up and is working well.  You are ready to get started.  The following files below are necessary to integrate into the notch base and then re-build notch.

In order to run this you need a working copy of the Nutch source and access to a Mongodb environment.

Folder Structure
----> java/org/apache/nutch/indexer/mongodb/MongodbConstants.java
----> java/org/apache/nutch/indexer/mongodb/MongodbIndexer.java
----> java/org/apache/nutch/indexer/mongodb/MongodbWriter.java
----> ivy/ivy.xml

Step 1. Create a new package called "java.org.apache.nutch.indexer.mongodb" and place the the files "MongodbConstants.java", "MongodbIndexer.java" and "MongodbWriter.java" in the package

Step 2. Open the ivy.xml and add the mongodb java driver dependency to the existing ivy/ivy.xml file.

Step 3. Rebuild and you should be ready to test

Step 4. To test you can run the following commands from terminal

Make sure you have seeded your crawl db with URLs

----> bin/nutch org.apache.nutch.indexer.mongodb.MongodbIndexer localhost crawl/crawldb crawl/linkdb crawl/segments/*
To see the available parameters

localhost - is the location of your mongodb database (used to connect)
crawldb - location of your crawled
linkdb - location of your linkdb
segments - location of your segments

----> Once you verified there are no errors, the data is being written to a db named "notch" and collection named "index" in Mongodb an you can verify the data by querying that collection