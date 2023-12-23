DATABASE SETUP AND MANAGEMENT USING AN ORM (SQLAlchemy)

# THE DATABASE:

## What a database is:
A binary file or collection of binary files stored in the file system. What makes these files unique is the way that we interact with them, including how we read and write to them. This is where the true defining feature of a database comes in. The DBMS!!

## What a DBMS is:
DBMS is short for DataBase Management System. In short, it is what makes a file or group of files into a database. These management systems all organize data in their own unique ways to optimize read and writes to the database. In our case, we are using Sqlite3 locally and Postgres in production.

# THE ORM:

## WHAT an ORM is:
The term ORM is short for Object Relational Mapper. It provides us with a convenient Object Oriented interface, with which we can interact with our database. It parses responses from the database into class instances that represent rows in our db.

### An Example Mapping:
When we fetch the Demo user from our database, we receive the packet below as the response.<br>

<img width="955" alt="db_select_response" src="https://github.com/crespohector/System-Design-Lecture-In-Mod-7/assets/107947798/37c5345f-3826-4e0a-94c4-78584b5acad3">

This packet has been formatted by the tool Wireshark and can be parsed as follows: On the far left, we simply have numbers of bytes in hexadecimal. So 0010 is actually the number 16. Each "line" consists of 16 bytes each in the center column. These are the raw bytes received by our client in hexidecimal notation. In the rightmost column we have a text representation of the packet. Note that many of the bytes in the packet are outside of the ASCII range and do not have glyph representations. These characters have been indicated with the strings of periods in the text '.....'. If we focus on the data portion of the packet, we see that 2 of the 4 PostgreSQL Headers represent the table row we queried for. The first, describes the table columns by name and the second provides the values for those columns in the row. Using this data in tabular format, SQLAlchemy can map the values to the respective keys and instantiate a class instance using this data! If we "unwind" the text representations of these 2 Headers we can loosely correlate the 2 as being 1 Header for "keys" and 1 being a Header with the "values" for those keys (Note: I believe the 'T' and the 'D' that begin the 2 headers are special control characters used by the PostgreSQL protocol but have not actually confirmed that...): 

<img width="1146" alt="row_description_and_row_data" src="https://github.com/crespohector/System-Design-Lecture-In-Mod-7/assets/107947798/ec64d017-8761-4641-9715-1ba5d95b4058">

Now that SQLAlchemy has the keys and the values that map to them, it can instantiate an object of class User, using these values, thereby providing us with a convenient Python object for us to interact with programmatically and ultimately return to the client side of our app. A class instance which we will turn into a dictionary as shown below:

```
{
  'id': 1,
  'username': 'Demo',
  'email': 'demo@aa.io'
}
```

Also by using the builtin methods, we are having our ORM write SQL queries for us.

# NETWORK:
Note that, while we are accustomed to communicating with our backend server from the client using HTTP Request / Responses,<br>
the way that our backend communicates with the database is a little different. Notably, it does NOT use the HTTP Protocol and instead<br>
each DBMS uses it's own proprietary protocol on top of the TCP / IP Protocol, which HTTP is also built on top of. In production we will see packets marked with PostgreSQL Headers!

# SQL:
