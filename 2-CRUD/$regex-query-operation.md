# $Regex Query Operation

## Question

Given the following example document:

```javascript
{
  "_id": ObjectId("5360c0a0a655a60674680bbe"),

  "user": {
    "login": "ir0n",
    "description": "Made of metal"
    "date": ISODate("2014-04-30T09:16:45.836Z"),
  }
}
```

and the following index:

```javascript
db.users.createIndex( { "user.login": 1, "user.date": -1 }, "myIndex" )
```

When performing the following query

```javascript
db.users.find( { "user.login": /^ir.*/ }, { "user":1, "_id":0 } ).sort( { "user.date":1 } )
```

Which of the following statements correctly describes how MongoDB will handle the query?

## Choices

**[O]As a covered query using "myIndex" because we are filtering out "_id" and only returning "user.login"**

[O] As an index scan that uses "myIndex" because field "user.login" is indexed

[X] As an optimized sort query (no explicit sort stage) using "myIndex" because we are sorting on an indexed field

[X] MongoDB will need to do a table/collection scan to find matching documents

## Detail Answers

Because the field user.login is indexed and the regex beginning of line operator is being used (^), the index myIndex will be used for this query.

Case insensitive regular expression queries generally cannot use indexes effectively. The $regex implementation is not collation-aware and is unable to utilize case-insensitive indexes.
