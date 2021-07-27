# Chuck Migration Procedure

## Question

When a chunk is in flight from one shard to another during a migration process, where are **reads** to that chunk directed?

## Choices

**[O] To the shared from which it is been migrated**

[X] To both the shared from which it is being migrated and the shared to which it is being migrated

[X] To the shared to which it is being migrated

[X] Document in the chuck are locked during migration. Reads are queued.

[X] To the config server

## Detailed Answer

When a chunk is in flight, reads and writes from the application can still access the documents in that chunk. Modifications on documents are propagated to the shard where it is migrated.

Until the chunk is fully migrated, the shard **(donor)** that is sending it to another shard (receiver) **is the only location where the all documents are present in their latest form**. For that reason, the donor shard is processing the reads.
