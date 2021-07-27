# Aggregation $sample  Operation

## Question

The users collection contains the following documents:

```javascript 
> db.users.find()
{ "_id" : 1, "name" : "dave123", "q1" : true, "q2" : true }
{ "_id" : 2, "name" : "dave2", "q1" : false, "q2" : false }
{ "_id" : 3, "name" : "ahn", "q1" : true, "q2" : true }
{ "_id" : 4, "name" : "li", "q1" : true, "q2" : false }
{ "_id" : 5, "name" : "annT", "q1" : false, "q2" : true }
{ "_id" : 6, "name" : "li", "q1" : true, "q2" : true }
{ "_id" : 7, "name" : "ty", "q1" : false, "q2" : true }
```

You perform the following query:

```javascript
db.users.aggregate( [ { $sample : { size : 3 } }
```

Which of the following are possible outputs from the database? 

## Choices

[O] 

{ "_id" : 7, "name" : "ty", "q1" : false, "q2" : true }

{ "_id" : 2, "name" : "dave2", "q1" : false, "q2" : false }

{ "_id" : 4, "name" : "li", "q1" : true, "q2" : false }

[O]

{ "_id" : 1, "name" : "dave123", "q1" : true, "q2" : true }

{ "_id" : 2, "name" : "dave2", "q1" : false, "q2" : false }

{ "_id" : 3, "name" : "ahn", "q1" : true, "q2" : true }

[O]

{ "_id" : 5, "name" : "annT", "q1" : false, "q2" : true }

{ "_id" : 6, "name" : "li", "q1" : true, "q2" : true }

{ "_id" : 7, "name" : "ty", "q1" : false, "q2" : true }

## Detail Answer

The $sample stage in the Aggregation Framework returns a subset of documents in a random fashion. In the above pipeline, we ask the stage to return 3 documents, so the documents returned could be any document in any order.
