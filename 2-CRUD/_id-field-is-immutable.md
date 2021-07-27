# _id Field is Immutable

## Qestion

Consider the following example document from the sample collection. All documents in this collection have the same schema. Which of the following queries will replace this with the document?

### From

``` json
{ "_id" : 3,  "a" : 7, "b" : 4 }
```

### To

 ``` json
 { "_id" : 7,  "c" : 4 }
 ```

## Choices

[X] db.sample.replaceOne({_id: 3}, {_id: 7, c: 4)})

[X] db.sample.updateOne({_id: 3}, {$set: {_id: 7, c: 4)}})

[X] db.sample.updateOne({_id: 3}, {_id: 7, c: 4, {$unset: ['a', 'b']}})

[X] db.sample.updateOne({_id: 3}, {_id: 7, c: 4)})
 
 **[O] This operation cannot be done with a single query**

 ## Detail Answer

 The _id field of a document is immutable
