# Icon and Term Definitions

This document explains the logic behind each icon and how the information was derived.

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

### Backup Redundancy
This is checking the backup redundancy setting of your Point in Time Recovery backups. Valid values are Local, Zone, and Geo. 

#### Local
This is locally redundant storage and it the least durable. As such we give this a "critical" icon.

#### Zone
This is zonally redudant storage and is durable across zone failures. This will protect you in zone level issues but will still fail in a regional outage. As such we give this a "warning" icon.

#### Geo
This is read accessible geo-redundant storage and is available even in the event of a regional failure. This is the highest level of protection and is denoted by a "success" icon.

### Zone Redundant HA
This is checking if one of the nodes of your SQL Azure Database is deployed to another zone. 

#### Warning Icon
When the warning icon is displayed Zone Redundancy is disabled and your database is succeptible to zonal failures.

#### Success Icon
When the success icon is displayed Zone Redundancy is enabled and your database is protected from zonal failures.

### Failover Group Enabled
This is checking if your SQL Azure Database is part of a Failover Group.

#### Warning Icon
When the warning icon is displayed if your database is not protected by a failover group and your database cannot be failed over during a regional failure.

#### Success Icon
When the success icon is displayed if your database is protected by a failover group and your database can be failed over during a regional failure.

### DB Is a Geo Replica
This checks if the database is a Geo Secondary replica or a primary database

#### Primary
This denotes the database is a single database without a replica or is the primary in a GeoDR group.

#### Geo Secondary
This denotes the database is a geo-replica secondary in a GeoDR group.

## SQL Managed Instance

### Backup Redundancy
This is checking the backup redundancy setting of your Point in Time Recovery backups. Valid values are Local, Zone, and Geo. 

#### Local
This is locally redundant storage and it the least durable. As such we give this a "critical" icon.

#### Zone
This is zonally redudant storage and is durable across zone failures. This will protect you in zone level issues but will still fail in a regional outage. As such we give this a "warning" icon.

#### Geo
This is read accessible geo-redundant storage and is available even in the event of a regional failure. This is the highest level of protection and is denoted by a "success" icon.

### Zone Redundant HA
This is checking if one of the nodes of your SQL Managed Instance is deployed to another zone. 

#### Warning Icon
When the warning icon is displayed Zone Redundancy is disabled and your managed instance is succeptible to zonal failures.

#### Success Icon
When the success icon is displayed Zone Redundancy is enabled and your managed instance is protected from zonal failures.

### Failover Group Enabled
This is checking if your SQL Managed Instance is part of an Auto Failover Group.

#### Warning Icon
When the warning icon is displayed if your managed instance is not protected by a failover group and your managed instance cannot be failed over during a regional failure.

#### Success Icon
When the success icon is displayed if your managed instance is protected by a failover group and your managed instance can be failed over during a regional failure.

## Cosmos DB