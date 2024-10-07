
# Icon and Term Definitions

This document explains the logic behind each icon and how the information was derived. Including more detailed information and resources for various service types.

[Common Terms](#common-terms)

[Azure SQL Database](#azure-sql-database)

[SQL Managed Instance](#sql-managed-instance)

[Cosmos DB](#cosmos-db)

## Common Terms

### Resource
This column named SQL Azure DB, Managed Instance, or Cosmos DB is the specific resource that is being checked.

### Region
The region the resource is deployed.

### Resource Group
The name of the resource group the resource is deployed.

### Subscription
The name of the subscription the resource is deployed.

## Azure SQL Database

### [Backup Redundancy](https://learn.microsoft.com/en-us/azure/azure-sql/database/automated-backups-overview?view=azuresql#backup-storage-redundancy)
This is checking the backup redundancy setting of your Point in Time Recovery backups. Valid values are Local, Zone, and Geo. 

#### Local
This is locally redundant storage and it the least durable. As such we give this a "critical" icon.

#### Zone
This is zonally redudant storage and is durable across zone failures. This will protect you in zone level issues but will still fail in a regional outage. As such we give this a "warning" icon.

#### Geo
This is read accessible geo-redundant storage and is available even in the event of a regional failure. This is the highest level of protection and is denoted by a "success" icon.

### [Zone Redundant HA](https://learn.microsoft.com/en-us/azure/azure-sql/database/high-availability-sla-local-zone-redundancy?view=azuresql&tabs=azure-powershell#zone-redundant-availability)
This is checking if one of the nodes of your SQL Azure Database is deployed to another zone. 

#### Warning Icon
When the warning icon is displayed Zone Redundancy is disabled and your database is succeptible to zonal failures.

#### Success Icon
When the success icon is displayed Zone Redundancy is enabled and your database is protected from zonal failures.

### [Failover Group Enabled](https://learn.microsoft.com/en-us/azure/azure-sql/database/failover-group-sql-db?view=azuresql)
This is checking if your SQL Azure Database is part of a Failover Group.

#### Warning Icon
When the warning icon is displayed if your database is not protected by a failover group and your database cannot be failed over during a regional failure.

#### Success Icon
When the success icon is displayed if your database is protected by a failover group and your database can be failed over during a regional failure.

### [DB Is a Geo Replica](https://learn.microsoft.com/en-us/azure/azure-sql/database/active-geo-replication-overview?view=azuresql&tabs=tsql#configure-geo-secondary)
This checks if the database is a Geo Secondary replica or a primary database

#### Primary
This denotes the database is a single database without a replica or is the primary in a GeoDR group.

#### Geo Secondary
This denotes the database is a geo-replica secondary in a GeoDR group.

## SQL Managed Instance

### [Backup Redundancy](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/automated-backups-overview?view=azuresql#backup-storage-redundancy)
This is checking the backup redundancy setting of your Point in Time Recovery backups. Valid values are Local, Zone, and Geo. 

#### Local
This is locally redundant storage and it the least durable. As such we give this a "critical" icon.

#### Zone
This is zonally redudant storage and is durable across zone failures. This will protect you in zone level issues but will still fail in a regional outage. As such we give this a "warning" icon.

#### Geo
This is read accessible geo-redundant storage and is available even in the event of a regional failure. This is the highest level of protection and is denoted by a "success" icon.

### [Zone Redundant HA](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/high-availability-sla-local-zone-redundancy?view=azuresql#zone-redundant-availability)
This is checking if one of the nodes of your SQL Managed Instance is deployed to another zone. 

#### Warning Icon
When the warning icon is displayed Zone Redundancy is disabled and your managed instance is succeptible to zonal failures.

#### Success Icon
When the success icon is displayed Zone Redundancy is enabled and your managed instance is protected from zonal failures.

### [Failover Group Enabled](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/failover-group-sql-mi?view=azuresql)
This is checking if your SQL Managed Instance is part of an Auto Failover Group.

#### Warning Icon
When the warning icon is displayed if your managed instance is not protected by a failover group and your managed instance cannot be failed over during a regional failure.

#### Success Icon
When the success icon is displayed if your managed instance is protected by a failover group and your managed instance can be failed over during a regional failure.

## Cosmos DB

### [Backup Policy](https://learn.microsoft.com/en-us/azure/cosmos-db/online-backup-and-restore#backup-modes)
This checks the backup policy of your Cosmos Database. Valid values are Periodic or Continuous.

#### Periodic
Periodic backups are taken based on a specific set rate. As this has large RPO implications we indicate this with the warning icon.

#### Continuous
Continuous backups are taken as changes are made and therefore have a very low RPO. As such we display the success icon.

### Backup Policy Health
This checks your individual backup settings and provides a health indicator depending on the level of risk. Valid values are Critical, Warning, and Healthy

#### Critical
This will only show if you are running periodic backups with a backup interval greater than 60 minutes or are not using geo replicated backups.

#### Warning
If you are running continuous backups, this will display if you are using the 7 day backup retention policy.

If you are running periodic backups, this will display if your backup interval is 60 minutes or less and you have geo replicated backups.

#### Healthy
This will only show if you have 30 day continuous backups.

### [Total Regions](https://learn.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally)
This is the count of total regions your Cosmos DB is currently available in. We will show the warning icon if you only have one region and the success icon if you have more than 1 region.

### Read Regions
This is the count of readable regions your Cosmos DB is currently available in. We will show the warning icon if you only have one region and the success icon if you have more than 1 region.

### Write Regions
This is the count of writable regions your Cosmos DB is currently available in. We will show the warning icon if you only have one region and the success icon if you have more than 1 region.

### [Zone Redundancy Health](https://learn.microsoft.com/en-us/azure/reliability/reliability-cosmos-db-nosql?toc=%2Fazure%2Fcosmos-db%2Ftoc.json#availability-zone-support)
This checks your zone redundancy settings for all your regions. Valid values are None, Some, and All.

#### None
This displays if none of your regions are configured for zone redundancy. We use the warning icon to indicate you do not have any zone redundancy.

#### Some
This displays if some of your regions are configured for zone redundancy. We use the warning icon to indicate that your zonal coverage is inconsistent.

#### All
This displays if all of your regions are configured for zone redundancy. We use the success icon to indicate you are fully covered in the event of a zonal outage.

###  [Consistency Level](https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels)
This is your default consistency level and is shown as it can have implications around how your data is stored and what data is available in other regions during an outage.