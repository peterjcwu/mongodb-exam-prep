# Query Optimizatioon

## Question

You have the following indexes on your collection:

```javascript
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "test.sample"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1,
			"date" : 1,
			"phone" : 1
		},
		"name" : "name_1_date_1_phone_1",
		"ns" : "test.sample"
	}
]
```

Which of the following queries will **use an index**? Check all that apply.

## Choices

**[O] db.sample.find({_id: 22, date: ISODate("2012-07-04")})** 

[O] db.sample.find({date: ISODate("2011-07-04", name: "Alice")})

[X] db.sample.find({title: "DBA"})

[X] db.sample.find({phone: "123-456-7890", info: "201-555-5972"})

## Detail Answer

There are two indexes
<code>{_id: 1}</code> and 
<code>{name: 1, date: 1, phone: 1}</code>

The order of the fields in the index is important, however, the order of the fields in the query are not significant as **the query planner will reorder the query terms** to match a prefix of, or the full compound index.

The query on _id will use the first index. Because _id is guaranteed to be unique, it's possible for the planner to make this optimization. To be sure, there will still be a FETCH stage to get the document and ensure the date predicate is fulfilled.

The query on date, name will also use an index, the name_1_date_1_phone_1 index, because a prefix is specified (name, date).

As for the query on phone and info, phone is indexed, however **as the third member of the compound index so won't be used**.
