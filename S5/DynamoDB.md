# DynamoDB

## Exam tips

- stored on SSD storgae
- spread across 3 geographically distinct data centres
- Eventual Consistent Reads(default)
- Strongly Consistent Reads

DynamoDB Accelerator (DAX)
- Fully managed, highly available, in-memory cache
- 10x performance improvement
- Reduces request time from milliseconds to microseconds - even under load
- no need for developers to manage caching logic
- compatible with dydb api calls

Transactions
- multiple "all-or-nothing" operations
- Financial transactions
- Fulfilling orders
- two underlying reads or writes - prepare/commit

On-demand Capacity
- pay-per request pricing
- Balance cost and performance
- no minimum capacity
- no charge for read/write - only storage and backups
- pay more per request than with provisioned capacity
- use for new product launches

On-demand Backup and Restore
- full backups at any time
- zero impact on table performance or availability
- consistent within seconds and retained until deleted

Point in time recovery (PITR)
- protects against accidental writes or deletes
- restore to any point in last 35 days
- incremental backups
- not enabled by default

