# RDS Backups, Mutil AZ & Read Replicas

## Exam tips

Backup
- Automated Backup
  - can recover db to any point in time within a 'retention period'
  - enabled default
  - stored in S3
  - storage space == size of db
  - schedule maintenance window 
- Databse Snapshots
  - manually
  - stored even after delete the original RDS instance

- Restoring Backups
  - stored into a new RDS instance with a new DNS endpoint

- Encryption At rest
  - MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora
  - done using KMS(Key Management Service) service

Multi-AZ
- used for Disaster Recovery
- force a failover form one AZ to another by rebooting the RDS instance

- exact copy of production db in another AZ
- RDS will automatically failover to the standby
- db operations can resume quickly without administrative intervention

- SQL, Oracle, MySQL, PostgreSQL, MariaDB
- XXXXX  Aurora XXXXX

Read Replica
- multi-az
- increase performance
- must have backups turned on
- can be in a different regions
- Oracle, MySQL, PostgreSQL, MariaDB, Aurora
- can be promoted to master, will break the read replica

- allow read-only copy of produciton db
- asynchronous replication from the primary RDS instance to the read replica

- Oracle, MySQL, PostgreSQL, MariaDB, Aurora
- used for scaling, not for DR
- must have automatic backups turned on in order to deploy a read replica
- 5 read replica copies of any db
- Each Read Replica will have its own DNS end point
- multi az available
- create read replica of multi-az source db
- can be promoted to be their own db
- can have read replica in a second region
