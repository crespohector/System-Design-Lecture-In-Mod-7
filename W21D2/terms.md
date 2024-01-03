# Terms

Data Definition Language (DDL) - A subset of SQL commands that pertain to the creation and management of database structures (tables, indexes). CREATE, ALTER, DROP, TRUNCATE, COMMENT.

Data Manipulation Language (DML) - A subset of SQL commands that pertain to the manipulation of data within the database. The simplest of which would be retrieval. SELECT, INSERT, UPDATE, DELETE.

Transaction Control Language (TCL) - A subset of SQL that pertains to the logical grouping of database queries. BEGIN, COMMIT, ROLLBACK.

Database Management System (DBMS) - A software system that is designed to manage and organize data in a structured manner. It allows users to create, modify, and query a database, as well as manage the security and access controls for that database.

Object Relational Mapper (ORM) - Connects object-oriented program (OOP) code with a database and simplifies relational database and OOP language interactions. We can write SQL queries by keying into class methods and we receive data from database queries as dictionaries.

Object Document Mapper (ODM): Provides an Object Oriented interface to accessing documents in a NoSQL database. Documents, while unstructured (we don't need to define attribute names or the number of such attributes), are formatted and so we need to interface with that particular document format. The most common format is JSON followed by BSON (binary) and sometimes even XML or YAML.

NoSQL (Not Only SQL): A category of databases that have flexible shemas. Meaning that records can be of various datatypes and sizes as opposed to the structured and pre-defined nature of Relational Databases. These types of databases can be sub-divided into 4 common architectures: Document Based (JSON, BSON, XML), Key-Value Store, Wide-Column, Graph based.
Notable Examples of each type:
Document Based: MongoDB, Elastisearch (AWS), CouchDB
Key-Value Store: IndexedDB, Redis, Memcached
Wide-Column: Cassandra, HBase
Graph Based: GraphDB, GraphQL, Neo4j

Transaction - A set of database operations that are grouped together as a single entity. If a single one of the opereations fail, it is the default behavior to ROLLBACK, ensuring that no changes to the database are made. This helps to ensure the integrity of data within the database.
