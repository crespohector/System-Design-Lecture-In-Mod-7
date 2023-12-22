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
When we fetch the Demo user from our database, we receive the packet below as the response.<br>

0000   1e 00 00 00 60 07 0d 00 01 49 06 40 00 00 00 00   ....`....I.@....
0010   00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 00   ................
0020   00 00 00 00 00 00 00 00 00 00 00 01 15 38 de dc   .............8..
0030   37 e4 a8 b1 ff 76 f4 40 80 18 18 cb 01 51 00 00   7....v.@.....Q..
0040   01 01 08 0a 35 1d b6 62 c7 60 b6 b5 54 00 00 00   ....5..b.`..T...
0050   88 00 04 75 73 65 72 73 5f 69 64 00 00 00 f7 d2   ...users_id.....
0060   00 01 00 00 00 17 00 04 ff ff ff ff 00 00 75 73   ..............us
0070   65 72 73 5f 75 73 65 72 6e 61 6d 65 00 00 00 f7   ers_username....
0080   d2 00 02 00 00 04 13 ff ff 00 00 00 2c 00 00 75   ............,..u
0090   73 65 72 73 5f 65 6d 61 69 6c 00 00 00 f7 d2 00   sers_email......
00a0   03 00 00 04 13 ff ff 00 00 01 03 00 00 75 73 65   .............use
00b0   72 73 5f 68 61 73 68 65 64 5f 70 61 73 73 77 6f   rs_hashed_passwo
00c0   72 64 00 00 00 f7 d2 00 04 00 00 04 13 ff ff 00   rd..............
00d0   00 01 03 00 00 44 00 00 00 8b 00 04 00 00 00 01   .....D..........
00e0   31 00 00 00 04 44 65 6d 6f 00 00 00 0a 64 65 6d   1....Demo....dem
00f0   6f 40 61 61 2e 69 6f 00 00 00 66 70 62 6b 64 66   o@aa.io...fpbkdf
0100   32 3a 73 68 61 32 35 36 3a 32 36 30 30 30 30 24   2:sha256:260000$
0110   6b 36 41 44 77 54 52 34 64 75 76 64 72 43 42 6e   k6ADwTR4duvdrCBn
0120   24 35 39 66 64 39 33 34 39 31 64 35 30 30 34 61   $59fd93491d5004a
0130   34 62 66 66 37 39 61 34 64 65 37 30 39 38 30 63   4bff79a4de70980c
0140   62 33 36 33 35 61 39 31 35 34 34 32 66 30 62 36   b3635a915442f0b6
0150   35 31 36 65 65 63 38 34 34 65 31 30 30 64 32 61   516eec844e100d2a
0160   34 43 00 00 00 0d 53 45 4c 45 43 54 20 31 00 5a   4C....SELECT 1.Z
0170   00 00 00 05 54                                    ....T

This packet has been formatted by the tool Wireshark and can be parsed as follows: On the far left, we simply have numbers of bytes in hexadecimal. So 0010 is actually the number 16. Each "line" consists of 16 bytes each in the center column. These are the raw bytes received by our client in hexidecimal notation. In the rightmost column we have a text representation of the packet. Note that many of the bytes in the packet are outside of the ASCII range and do not have glyph representations. These characters have been indicated with the strings of periods in the text '.....'. If we focus on the data portion of the packet, we see that 2 of the 4 PostgreSQL Headers represent the table row we queried for. The first, describes the table columns by name and the second provides the values for those columns in the row. Using this data in tabular format, SQLAlchemy can map the values to the respective keys and instantiate a class instance using this data! 


# NETWORK:
Note that, while we are accustomed to communicating with our backend server from the client using HTTP Request / Responses,<br>
the way that our backend communicates with the database is a little different. Notably, it does NOT use the HTTP Protocol and instead<br>
each DBMS uses it's own proprietary protocol on top of the TCP / IP Protocol, which HTTP is also built on top of. In production we will see packets marked with PostgreSQL Headers!

# SQL:
