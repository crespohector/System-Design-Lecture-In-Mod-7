# Choosing a Database (Management System) and ORM.
## Challenges
We shall discuss the design considerations that go into assessing our application's needs and what database technologies are best suited to our use case.

### What is a database?

### What is a DBMS?

### What kind of DBMS should we choose?

### What database are we using in our production environment?

### What database are we using in our development environment?

### What protocol are we using when interacting with our database?

### What are database "transactions"?

### How will we communicate with the database?

### What is an ORM?

### Why should we use an ORM?

### A general rule (The Many-to-Many Rule) for selecting a database for your application:
* Document Based (NoSQL): Choose this architecture when your data contains little to no relationships and NO Many-to-Many relationships.
* Relational: Choose this architecture when your data has numerous relationships, but when only a couple of them would be considered Many-to-Many.
* Graph Based (NoSQL): Choose this architecture when your data has numerous Many-to-Many relationships!
