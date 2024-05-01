# SQL

SQL databases, known as RDBMS (Relational Database Management System) or just Relational databases, is one of many types of databases, that persist its data into the disk into tables and tables fields.

## Tables

Tables are a structured schema, defined by fields, these fields follow strict rules for each of them, defining its types, length, and other constraints.

    CREATE TABLE planet(
        stellar_code varchar(32) NOT NULL PRIMARY KEY,
        name varchar(30) NOT NULL,
        category varchar(13) DEFAULT 'uncategorized',
        system_code int NOT NULL,
        FOREIGN KEY (system_code) REFERENCES solar_system(system_id)
    );

    CREATE TABLE solar_system(
        system_id int NOT NULL PRIMARY KEY,
        name varchar(30) NOT NULL,
        num_planets int DEFAULT 0
    );

As you can see, we can persist our data into very organized structures, and linking them using references to sibling tables using a foreign key.
This will allow us to read that data in a meaningful way using join operations in our query statments.

    SELECT 
        planet.name, planet.category, solar_system.name
    FROM
        planet
    JOIN
        solar_system
    ON
        planet.system_code = solar_system.system_id;

## Why Relational databases?

Relational databases are very strict due to its policies/properties known as ACID.

- Atomicity
- Consistency
- Isolation
- Durability

The policies are special properties that defined what we call transactions.

Transactions are a sequence of staments that occurs into the database, which perform many sort of operations, from insertion, to deletion.

## Atomicity

Atomicity ensures that everything is successfully finished in a transaction, or none will be.
Imagine you have a collection of data that is going to be persisted, like our planet and solar_system example.
Imagine we have to persist our solar_system first, and then persist our planet data. If something goes wrong during the planet insertion the Atomicity policy rolls back the entire transaction, which means, the system return to its initial state before the transaction begins.

In the context of a transaction it follows a specific flows.

ex. Successfull

    BEGIN -> COMMIT

ex. Failure

    BEGIN -> FAILURE! -> ROLL BACK

## Consistency

Consistency ensures that our defined table constraints are followed as modeled, such as primary key, foreign key, unique, etc.
For example, if a table defined that one table field should not be null a transaction respectst that policy, otherwise it returns an errors to its client.
In other words, transactions must to ensure the database will leave from a valid state to another.

## Isolation

Isolation policy will ensure that each transaction is completely isolated from another, without affecting the results of the already running transaction.
Although concurrent transactions will run in a sequencial way in cases that may occur dirty read. This means, if a transaction is performing an update in one record, and a second transaction is trying to read that data, the Isolation policy will wait until the update is done before the second one try to read from it.

## Durability

The last, Dirability policy ensures that no matter if a failure in the system occurs, the data still able to be read later.
For example, if a system crash, data stored in the momory is wiped out, while data store in the disk is not.

## Trade-offs

While SQL databases deliver policies that may be a good requirement for the overal system(ACID), it has its limitations such as scalability, and flexibility.

SQL databases are not designed for horizontal scale in mind. This can lead to two problems, high cost to vertical scale its server, and single point of failure, since it rely on a single server to run it.
Although some cloud providers has done some upgrades in some of these databases, allowing them to achieve scalability and high availability.

As mentioned SQL databases are very strict due to schema constraints, so if your system requires some sort of flexibility it may not be the ideal choice. Imagine requirements that you may want to store data that is not already mapped, or you may expect eventual consistency.

Data relationship can become easily complex due to data normalization, when querying these data many joins will be required, which is a very expensive operation, this can lead to bottonecks to the system as data grows and tables become larger and larger. Although you can minimize its impact leveraging from indexing, and denormalization techniques.

Also, relational databases is not the ideal choice for handling big data, which stores very large datasets.
As mentioned, when data tables grows and the volume of the data grows as well, we may expect some sort of flexibility and also horizontal scalability to perform distributed computation over the data. Which SQL databases do not deliver.
