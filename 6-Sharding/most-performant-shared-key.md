# Most Performant Shard Key

## Question

Your top three queries for a collection consist of the following query patterns:

```javascript
90% db.employees.find( { lastName : 1, firstName : 1, currentEmployee : 1, company : 1 }, { supervisor : 1, teamName : 1, position: 1, duties : 1, salary : 1 } )

5% db.employees.updateOne( { employeeId: 1 }, { $set : { position : 1, teamName : 1, salary : 1, duties : 1 } } )

1% db.employees.updateOne( { employeeId: 1 }, { $set : { currentEmployee : 1, hireDate: 1 } } )
```

Your system is outgrowing the servers you currently have it running on, and you’d like to shard the collection. Which of the following shard keys will be most performant?

## Choices

**[O] {company: 1, lastName: 1}**

[X]  {supervisor: 1, teamName: 1, position: 1, duties: 1, salary: 1}

[X] {employeeId: 1}

[X] {currentEmployee: 1, hireDate: 1}

**[X] {currentEmployee: 1, company: 1}**

## Detailed Answer

Because the first query account for 90% of your read workload, it should be the one driving the selection of the shard key.

Combination of fields from that query would make the best shard key. Out of the two solutions that use a subset of those fields, the one using company and lastName is preferred to currentEmployee and company, as the **currentEmployee field is likely a boolean** leading to few values, and potentially a lot of documents with the same values, resulting in jumbo chunks (chunks too big to be splitted).
