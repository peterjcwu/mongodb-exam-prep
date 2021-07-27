# Covered Query

A covered query is a query that can be satisfied entirely using an index and does not have to examine any documents. An index covers a query when all of the following apply:

1. All the fields in the query are part of an index, and
2. All the fields returned in the results are in the same index.
3. No fields in the query are equal to null (i.e. {<code>"field" : null}</code> or <code>{"field" : {$eq : null}}</code> ).

## Question

Which of the following must be true for a query to be a covered query? Check all that apply.

## Choices

[O]  All fieldl used in the selection filter of the query must be in the index that the query uses

<strong>[O] All fields returned in the reuslts must be in the index that the query uses</strong>

[x] All fileds returned in the results must be fields in the selection filter of the query 
