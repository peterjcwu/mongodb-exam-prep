# Question

Which of the following statements are true of **unique indexes**? Check all that apply.

#  Choices

[X] The only possible unique index is the "_id" filed

[O] The "unique" constrain on the index ensures that no two (or more) documents can share a value for that field in a collection

**[O] hashed index cannot be unique**

# Detail Answer

#### To create an unique  index

``` javascript
db.collection.createIndex( <key and index type specification>, { unique: true } )
```

#### Restrictions

1. MongoDB cannot create a unique index on the specified index field(s) if the collection already contains data that would violate the unique constraint for the index.
2. You may not specify a unique constraint on a hashed index.

#### Hashed Index

Hashed indexes maintain entries with hashes of the values of the indexed field.

db.collection.createIndex( { _id: "hashed" } )

MongoDB supports hashed indexes of any single field. The hashing function collapses embedded documents and computes the hash for the entire value, but does NOT support multi-key (i.e. arrays) indexes.
