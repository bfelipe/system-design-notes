# NoSQL (Not Only SQL)

NoSQL databases are another type of databases that was designed to solve problems that SQL databases could not, such as big data, horizontal scale, and data flexibility.

There are four types of NoSQL databases:

- Key/Value store
- Document store
- Wide Column store
- Graph store

## Key/Value store

Key/Value store is one type of NoSQL database, which allow you to store data using the unique property as a key, and the entire data payload as a value. Searching is very optmized since it rely on a data structure such as maps which can delivery an O(1) time complexity.
An example of such database is Redis. Although Redis stores data into the memory, different than other NoSQL databases that store its data into the disk.

## Document store

Document store allow you to persist its data as a single file in a familiar structure that applications can work on, such as json. It organize these files into collections, which is something similar to folders.
This type of database is designed for horizontal scale, and data flexibility, which is common into big data scenarios.
MongoDB is a good example of a Document database.
It's important to say also, Document stores are good candidates to deliver eventual consistency, due to its distributed design.

## Wide Column store

Wide Column store is a peculiar database, that prefer to organize related data into columns instead of rows.
It is structured as column families, each containing a different set of attributes, which is dynamic, organized as key/value structure.
Besides its data flexibility, Wide Column store are also efficient on writing and reading data due to the way data is organized.
In scenarios of big data analysis and distributed systems, this may be a good database that will easily handle high volume of data.
Wide Columns store are designed considering horizontal scalability, eventual consistency and fault tolerance.

ex. User data into wide column store


| Row Key    | Column Family: User_Info            | Column Family: User_Activity         |
|------------|------------------------------------|--------------------------------------|
| User_ID_1  |                                    | Last_Login: 2024-04-28 10:30:00 UTC  |
|            | Name: John Doe                     | Total_Logins: 50                     |
|            | Age: 30                            |                                      |
|            | Email: john@example.com            |                                      |
|------------|------------------------------------|--------------------------------------|
| User_ID_2  |                                    | Last_Login: 2024-04-29 15:45:00 UTC  |
|            | Name: Jane Smith                   | Total_Logins: 75                     |
|            | Age: 25                            |                                      |
|            | Email: jane@example.com            |                                      |

## Graph store

Graph store is another peculiar database, which is designed to solve problems of efficient data querying over complex data relationships.
It is structured as a graph ds, which each node represents the entire entity, and edges are used to connect nodes by their relantionship, each node can contain many different categories of edge relantionships.
Systems such map app, social media, media content management, search engine are examples of systems that benefit from this sort of databases.

## Why NoSQL?

NoSQL shines where SQL dabatases can't opperate well.
It provides data flexibility, and is designed to horizontal scale by default, it also allow to store that into distributed servers, which part of its data may be located in one region, while another portion is stored in another region.
While relational databases rely on ACID policies, NoSQL works on BASE in mind.
BASE stands for "Basically Available, Soft state, Eventual consitency".

## Eventual consistency

Eventual consistency rely on the master/slave or primary/replicas pattern architecture, which data is written in one server node, and eventually distributed across its replicas.
This pattern remove the huge amount of read into a single server, while this may add some delay while trying to read the data on nodes which it is not stored yet, although it minimize point of failure effects.
If a primary server node goes down, one of the replicas servers are selected to be the new primary server, while another replica instance is turn up to replace its place, maintaing fault tolerance and data consistency.
