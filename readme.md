# Apache Cassandra

Apache Cassandra is an open-source distributed NoSQL database system designed to handle large amounts of data across many commodity servers, providing high availability and fault tolerance with no single point of failure. It was initially developed at Facebook and is now maintained by the Apache Software Foundation.

Cassandra is designed to handle structured, semi-structured, and unstructured data with a highly scalable architecture that can be easily distributed across multiple nodes. It provides support for ACID transactions, with strong consistency guarantees, and can handle read and write operations at a massive scale.

Cassandra's benefits over other databases include its decentralized architecture, allowing it to distribute data across many nodes and maintain high availability and fault tolerance. Cassandra also offers tunable consistency levels, allowing developers to trade off consistency for performance in certain use cases.

Cassandra is widely used in industries such as finance, healthcare, e-commerce, and social media for its high availability, scalability, and fault-tolerance features.

## Table of Contents:

- [Introduction](#apache-cassandra)
- [Cassandra Architecture](#cassandra-architecture)
- [Installing Apache Cassandra](#installing-apache-cassandra)
- [Cassandra Data Model](#cassandra-data-model)
- [CQL (Cassandra Query Language)](#cql-cassandra-query-language)
- [Cassandra Cheat Sheet](#cassandra-cheat-sheet)
- [Cassandra Real-World Use Cases](#cassandra-real-world-use-cases)

## Cassandra Architecture

Cassandra follows a decentralized architecture, where each node in the cluster has an equal role and there is no single point of failure. Data is replicated across multiple nodes, with each node responsible for storing a subset of the data. The replication factor can be configured to ensure data durability in case of node failures.

Cassandra uses a peer-to-peer gossip protocol to maintain cluster membership, detect node failures, and disseminate information about the cluster. It also uses a consistent hashing algorithm to distribute data across the cluster, which allows for easy addition or removal of nodes without having to rebalance the entire cluster.

## Installing Apache Cassandra

To install Apache Cassandra, follow these steps:

1. Download the latest version of Apache Cassandra from the official website.
2. Extract the downloaded file to a desired location on your system.
3. Open the extracted folder and navigate to the 'conf' directory.
4. Open the cassandra.yaml file and modify the following parameters:
   - `cluster_name:` Set a unique name for your cluster.
   - `seeds:` Add the IP address of at least one node in your cluster.
   - `listen_address:` Set the IP address of the node.
   - `rpc_address:` Set the IP address of the node.
   - `endpoint_snitch:` Set the endpoint snitch to 'SimpleSnitch'.
5. Save the changes to the cassandra.yaml file and close it.
6. Start the Cassandra server by running the following command from the bin directory:

```bash
 ./cassandra -f
```

The `-f` option starts the server in the foreground and allows you to monitor the server logs for any errors or warnings.

## Cassandra Data Model

Cassandra's data model is based on a key-value pair system, with a column-oriented storage architecture. Data is organized into tables, with each table consisting of partitions and rows. Each partition is uniquely identified by a partition key, which can be composed of one or more columns. Within each partition, rows are identified by a clustering key. Columns are further divided into two types: static columns and dynamic columns.

Static columns have the same value for each row in a partition, while dynamic columns can have different values for each row. Columns are organized into column families, which are similar to tables in a relational database.

Cassandra also supports the concept of collections, which are used to store multiple values within a single column. Collections can be of various types, such as lists, sets, and maps. For example, a set can be used to store a list of email addresses associated with a user.

## CQL (Cassandra Query Language)

CQL is a query language used to interact with Cassandra's data model. It is similar to SQL in syntax, but with some differences due to Cassandra's column-oriented data model. Here are some basic CQL commands:

#### ~ Creating a keyspace:

```bash
 CREATE KEYSPACE <keyspace_name> WITH replication = {'class': 'SimpleStrategy', 'replication_factor': <num_of_replicas>};
```

#### ~ Using a keyspace:

```bash
 USE <keyspace_name>;
```

#### ~ Creating a table:

```bash
 CREATE TABLE <table_name> (<column_name> <data_type> PRIMARY KEY);
```

#### ~ Inserting data into a table:

```bash
 INSERT INTO <table_name> (<column_name>, <column_name>, ...) VALUES (<value>, <value>, ...);
```

#### ~ Querying data from a table:

```bash
 SELECT * FROM <table_name> WHERE <column_name> = <value>;
```

#### ~ Updating data in a table:

```bash
 UPDATE <table_name> SET <column_name> = <new_value> WHERE <column_name> = <old_value>;
```

#### ~ Deleting data from a table:

```bash
 DELETE FROM <table_name> WHERE <column_name> = <value>;
```

## Cassandra Cheat Sheet

Here is a quick reference guide to some important Cassandra commands:

| Title                              | Command                                                                                                                  |
| :--------------------------------- | :----------------------------------------------------------------------------------------------------------------------- |
| Starting Cassandra:                | ./cassandra -f                                                                                                           |
| Connecting to Cassandra using CQL: | cqlsh                                                                                                                    |
| Creating a keyspace:               | CREATE KEYSPACE <keyspace_name> WITH replication = {'class': 'SimpleStrategy', 'replication_factor': <num_of_replicas>}; |
| Using a keyspace:                  | USE <keyspace_name>;                                                                                                     |
| Creating a table:                  | CREATE TABLE <table_name> (<column_name> <data_type> PRIMARY KEY);                                                       |
| Inserting data into a table:       | INSERT INTO <table_name> (<column_name>, <column_name>, ...) VALUES (<value>, <value>, ...);                             |
| Querying data from a table:        | SELECT \* FROM <table_name> WHERE <column_name> = <value>;                                                               |
| Updating data in a table:          | UPDATE <table_name> SET <column_name> = <new_value> WHERE <column_name> = <old_value>;                                   |
| Deleting data from a table:        | DELETE FROM <table_name> WHERE <column_name> = <value>;                                                                  |
| Creating an index:                 | CREATE INDEX <index_name> ON <table_name> (<column_name>);                                                               |
| Compacting a table:                | nodetool compact <keyspace_name> <table_name>;                                                                           |
| Repairing a table:                 | nodetool repair <keyspace_name> <table_name>;                                                                            |
| Checking the status of a node:     | nodetool status;                                                                                                         |
| Checking the status of a cluster:  | nodetool ring;                                                                                                           |

## Cassandra Real-World Use Cases

- **Social media:** Cassandra is used by social media platforms like Facebook and Twitter to store large volumes of data, including user profiles, social graphs, and activity streams. Cassandra's ability to handle high write throughput and provide low-latency access to data makes it a great fit for social media use cases.

- **E-commerce:** Online retailers like eBay and Amazon use Cassandra to store product catalogs, user profiles, and transactional data. Cassandra's ability to provide high availability and scalability makes it an ideal choice for e-commerce applications that need to handle large volumes of traffic.

- **IoT:** The Internet of Things (IoT) generates massive amounts of data from sensors and devices. Cassandra is used to store this data, process it in real-time, and provide insights to users. Companies like Philips and Cisco use Cassandra to power their IoT platforms.

- **Finance:** Financial institutions like JPMorgan Chase use Cassandra to store and manage data related to trades, positions, and risk. Cassandra's ability to provide high availability and fault tolerance is critical in the finance industry, where downtime can result in significant financial losses.

- **Healthcare:** Healthcare organizations like the Centers for Disease Control and Prevention (CDC) use Cassandra to store and analyze data related to disease outbreaks and public health trends. Cassandra's ability to handle large volumes of data and provide real-time insights is crucial in the healthcare industry.

## Conclusion

Apache Cassandra is a highly scalable distributed NoSQL database system designed to handle large amounts of data across many commodity servers. It provides high availability and fault tolerance with no single point of failure, making it ideal for industries such as finance, healthcare, e-commerce, and social media. Cassandra's decentralized architecture allows it to distribute data across many nodes and maintain high availability and fault tolerance. It offers tunable consistency levels, allowing developers to trade off consistency for performance in certain use cases. Cassandra's data model is based on a key-value pair system with a column-oriented storage architecture, and CQL is used to interact with the data model. Overall, Cassandra is a powerful tool for managing large amounts of data at scale.
