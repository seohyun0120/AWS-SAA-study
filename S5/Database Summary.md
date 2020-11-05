# Database Summary

## Exam tips

RDS (onlie transaction processing)
-  SQL
-  MySQL
-  PostgreSQL
-  Oracle
-  Aurora
-  MariaDB

DynamoDB(NoSQL)
Redshift OLAP (online analytic processing)

Elasticache
- memcached: simple
- redis: backup, multi AZ, detailed

- RDS runs on virtual machines 
- cannot log in to these operating systems
- patching is Amazon's responsibility
- RDS is not serverless, Aurora is

- backups for RDS
  - Automated
  - Database snapshots

Read replicas
- multi AZ
- used to increase performace
- must have backups turned on
- can be in different regions
- can be MySQL, PostgreSQL, MariaDB, Oracle, Aurora
- can be promoted to master, will break the read replica

MultiAZ
- used for data recovery 
- force failover from one AZ to another by rebooting the RDS instance

- Encryption at rest is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora
- done using AWS Key Management Service service
- data stored at rest in the underlying storage is encrypted
- automated backups, read replicas, snapshots

DynamoDB
- SSD storage
- spread across 3 geographically distinc data centres
- eventual consisten reads (default)
- strongly consistent reads

Redshift
- only 1 AZ
- used for business intelligence
- backups
  - default with a 1 day retention pewwd
  - maximum retention 35 days
  - redshift always attempts to maintain at least three copies of your drata
  - asynchronosly replicate snapshots to S3 in another region for DR

Aurora
- 2 copies of your data are contained in each AZ, with minimum of 3 AZ. 6 copies of data
- share with other AWS Accounts
- 3 types of replicas available.
- Aurora has automated backups turned on by default
- also take snapshots with Aurora
- can share these snapshots with other AWS Accounts
- use aurora serverless if you want a simple, cost-effective option for infrequent, intermittent, unpredicatble workloads

Elasticache
- increase web applicaiton preformance
- Redis: Multi Az
- backup and restore of Redis
- need to scale horizontally -> memcached