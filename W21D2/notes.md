DATABASE SETUP AND MANAGEMENT USING AN ORM (SQLAlchemy)

# THE DATABASE:

## What a database is:
A binary file or collection of binary files stored in the file system. What makes these files unique is the way that we interact with them, including how we read and write to them. This is where the true defining feature of a database comes in. The DBMS!!

## What a DBMS is:
DBMS is short for DataBase Management System. In short, it is what makes a file or group of files into a database. These management systems all organize data in their own unique ways to optimize read and writes to the database. In our case, we are using Sqlite3 locally and Postgres in production.

# THE ORM:

## WHAT an ORM is:
The term ORM is short for Object Relational Mapper. It provides us with a convenient Object Oriented interface, with which we can interact with our database.
By using the builtin methods, we are having it write SQL queries for us.
It also parses the response from the database into class instances that represent rows in our db.

### An Example Mapping:
When we fetch the Demo user from our database, we receive this text as the response.


# NETWORK:
Note that, while we are accustomed to communicating with our backend server from the client using HTTP Request / Responses,<br>
the way that our backend communicates with the database is a little different. Notably, it does NOT use the HTTP Protocol and instead<br>
each DBMS uses it's own proprietary protocol on top of the TCP / IP Protocol, which HTTP is also built on top of. In production we will see packets marked with PostgreSQL Headers!

# SQL:
