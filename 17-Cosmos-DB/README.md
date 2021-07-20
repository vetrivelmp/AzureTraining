# Miscellaneous
## Cosmos DB
- Quick primer on NoSQL Databases
- Introduction to Cosmos DB
- Azure Cosmos DB - SQL API
- Partitioning in Azure Cosmos DB
- Understanding the Item id property
- More on querying data in Cosmos DB
- Azure Cosmos DB - Embedding data
- Azure Cosmos DB - Referencing data
- Introduction to Change Feed, Stored Procedures, Triggers
- Azure Cosmos DB - Change Feed
- Azure Cosmos DB - Stored Procedures
- Azure Cosmos DB - Triggers
- Azure Cosmos DB - Local Emulator
- Azure Cosmos DB - Synthetic Partition Key
- Azure Cosmos DB - Time to Live
- Azure Cosmos DB - Indexing
- Use case scenario - Sending data to Cosmos DB
- Diagnostics Data
- Replicating data globally
- Consistency Levels
- Consistency Level - Setting the level
- Azure CLI commands for Azure Cosmos DB
- Azure Cosmos DB - Table API


## Azure Cosmos DB - SQL API
- database name: appdb
- container name: customer

### Add items to container
```
{
"customerid":"C1",
"customername":"UserA"
}
```

```
{
"customerid":"C2",
"customername":"UserB",
"orders":[
{"orderid":"O1","course":"AZ-104","price":100}
]
}
```

```
{
"customerid":"C3",
"customername":"UserC",
"orders":[
{"orderid":"O2","course":"AZ-104","price":50},
{"orderid":"O3","course":"AZ-204","price":80}
]
}
```

### Querying
```
SELECT * FROM c.orders
```

```
SELECT o.orderid, o.course FROM o IN course.orders where o.course='AZ-204'
```
