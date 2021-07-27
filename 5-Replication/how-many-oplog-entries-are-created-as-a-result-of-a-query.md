# How Many Oplog are Created as a Result of a Query

## Question

The people collection contains the following documents:

```javascript
{ "_id" : ObjectId("57fd59a2d630a0fd9685a148"), "firstName" : "Arthur", "lastName" : "Aaronson", "state" : "WA", "city" : "Seattle", "likes" : [ "dogs", "cats" ] }
{ "_id" : ObjectId("57fd59a2d630a0fd9685a149"), "firstName" : "Beth", "lastName" : "Barnes", "state" : "WA", "city" : "Richland", "likes" : [ "forest", "desert" ] }
{ "_id" : ObjectId("57fd59a2d630a0fd9685a14a"), "firstName" : "Charlie", "lastName" : "Carlson", "state" : "CA", "city" : "San Diego", "likes" : [ "desert", "beach" ] }
{ "_id" : ObjectId("57fd59a2d630a0fd9685a14b"), "firstName" : "Dawn", "lastName" : "Davis", "state" : "WA", "city" : "Seattle", "likes" : [ "forest", "mountains" ] }
```

You perform the following query:

```javascript
db.people.deleteMany( { state : "NB" } ) 
```

How many oplog entries are created as a result of this query?


## Detail Answer

**0**

The Oplog collection only contains an entry for a given write query if the operation has modified a document.

Because the deleteMany operation is not deleting any document, there will be no Oplog entry to record.
