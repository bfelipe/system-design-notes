# Data Replication & Sharding

Replication and Sharding are techniques applied into distributed systems which aims to provide high availability and throughput over data.

## Replication

This technique rely on the primary/replica architecture.
Each time a transaction is successfully commited into the primary server, it is send to its replicas.
There are different ways to apply Data Replication:

- Synchronous Replication
- Asyncronous Replication
- Multi-Master Replication

## Synchronous Replication

In this approach, data is persisted into the primary server, followed by a sync event for the replicas. If there are two different clients connected to each server, one into the primary server, and the second one connected to the replica, the second one will be able to access the data consistent with the primary server first. This occurs because the primary server will only return a response to its user, once the replication is complete, in other words, this technique adds latency over real-time replication.
If the primary server goes down, the most updated server becomes the new primary node, and a new replica is deployed.

![](/images/9.png)

## Asynchronous Replication

In this approach, data is persisted into the primary server, but instead of updating its replicas in real-time, our primary server send the data to its replicas, without waiting a response or acknoledge of updated data has been applied.
In this case, latency doesn't occur as in the synchronous replication, but it may have a delay of accessing its data is a client try to access it from a replica node. In other words, availability is aimed instead of data consistency.

## Multi-Master Replication

Lastly we have Multi-Master Replication, which consists having multiple primary nodes followed by its replicas.
This approach is often used in scenarios where data is supposed to be available in different regions. Although, synchronizing data into multiple primary server may add a challenge due its read/write among the servers, which increase latency and periodic updates are necessary to ensure data consistency.

![](/images/10.png)

## Sharding

Sharding is a technique which applyed on dealing with high traffic on a database server when data replication isn't enough.
In sharding, our database is divided/partitioned into small parts, each one having its own server.

When data is splitted, data groups are formed based on a unique factor called a shard key. This key determines which shard data belongs to or where it should be stored.

For example, imagine you have a system which is available to an entire country. Instead of storing your data into a single server you can choose to create different partitions/shards for each state/province of that country. This decision is made on having each state/province as your shard key.

Sharding will increase performance, scalability and availability as well by distributing the workload into multiple servers.

Although, in order to achieve sharding properly in a SQL database, engineers will need to implement its mechanisms in the application level, properly distributing data over the tables in their own partitions, which can be a challenge.

NoSQL databases are better options to use sharding since it is natively implemented, which can make easy to handle large datasets since you are not limited to data constraints as SQL databases impose.
