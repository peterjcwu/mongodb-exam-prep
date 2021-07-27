# Best Shard Key
Why is picking a good shard key so tricky and so important? A number of reasons:

+ If you pick the wrong shard key, you can totally trash the performance of your cluster
+ Sharding a collection is a one-way parachute jump; if you get it wrong, you’ll need to migrate the data to a new collection with the right shard strategy.
+ Picking the right shard key is more of an art than a science; there are 5 different considerations, and may not be possible to satisfy them all
  
### The Perfect Shard Key
If you think about it, the perfect shard key would have the following characteristics:

+ All inserts, updates, and deletes would each be distributed uniformly across all of the shards in the cluster
+ All queries would be uniformly distributed across all of the shards in the cluster
+ All operations would only target the shards of interest: an update or delete would never be sent to a shard which didn't own the data being modified
+ Similarly, a query would never be sent to a shard which holds none of the data being queried  

# Question
Consider a collection of users with the following fields and possible values:

+ **phone_number** -- a 10-digit telephone number (string)
+ **eye_color** -- "brown", "hazel", "blue", "green", or "other" (string)
+ **weight** -- an integer in pounds; known for about half the users
+ **started_driving_at** -- the age at which the user got their driver's license in years. For most users this is 15, 16, 17, or 18. (integer)
+ **_id** -- automatically created on insert (ObjectId)

Assuming the data-access patterns also support your choice, which of these fields would make the best shard key?

## Choices
[O] phone_number

[X] eye_color

[X] weight
  
[X] started_driving_at

[X]_id

## Detailed Answer
Phone number is the best selection here.

With weight, eye_color, and started_driving_at, we run the risk of low cardinality and wouldn't get a good distribution.

_id would not make a good shard key because it isn't something meaningful we could query the database with in normal circumstances, like searching for a customer record when they call into a call center.
