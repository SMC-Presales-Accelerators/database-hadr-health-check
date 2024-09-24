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

## SQL Managed Instance

## Cosmos DB