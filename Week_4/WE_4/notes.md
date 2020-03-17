# we4

## rdbms
Relational database management systems (RDBMS)
- Vendors: On the commercial side, Oracle Database, IBM DB2, and Microsoft SQL Server are three well known solutions. On the free and open source side, MySQL, SQLite, and PostgreSQL are three widely used solutions.

## sql
- learn more at about sql at [kahn academy](https://www.khanacademy.org/computing/computer-programming/sql)
- learn by doing tutorials at [sqlzoo](https://sqlzoo.net/wiki/SQL_Tutorial)
- Once you've downloaded and set up an RDBMS on your system, the next step is to create a database and tables inside of it in order to insert and manage your relational data. The way you do this is with Structured Query Language (SQL), which is the standard language for working with RDBMSs.
- SQL is pretty similar to regular English sentences. There are small variations in SQL between each RDBMS vendor, termed SQL dialects, but the differences are not dramatic enough that you can't easily transfer your SQL knowledge from one to the other.
### Create a database, named "development"
  * `CREATE DATABASE development;`
### Create a table named "users"
  * RDBMSs require that each column in a table is given a data type. Here I've assigned the "full_name" and "username" columns the data type VARCHAR which is a string that can vary in width. I've arbitrarily set a max length of 100. A full list of data types can be found [here](https://en.wikipedia.org/wiki/SQL#Data_types).
  * `CREATE TABLE users (
  full_name VARCHAR(100),
  username VARCHAR(100)
);`
  * for id's the data type shuld be `INTGER PRIMARY KEY` by adding `AUTOINCREMENT` to `INTGER PRIMARY KEY AUTOINCREMENT` you no longer need to specify the id for every new entry and the sytem will automatically add an id one bigger than the curretn largest id
  * THE AUTO-INCREMNT feature in POSTGRESQL is `SERIAL PRIMARY KEY`. the keyword `SERIAL` is a pseudo-class for integer that is never null and will increase automatically btu the value type is still an `INTEGER`
### Insert a record (the Create operation in CRUD)
  * `INSERT INTO users (full_name, username)
VALUES ("Boris Hadjur", "_DreamLead");`
### Retrieve all tweets belonging to @_DreamLead (the Retrieve operation in CRUD)
  * `SELECT text, created_at FROM tweets WHERE username="_DreamLead";`
  * if you want to query everything from table use `SELECT *`
  * `SELECT * FROM groceries WHERE aisle > 5 ORDER BY aisle;`
    * `WHERE` can be used to filter out data
    * `ORDER BY` can be used to sort data (ascending/descending)
    * `LIKE "B%"` where `%` is a wild card and will select anythign that starts with B. 
      * `"%B"` will select anything that ends with B. 
      * `"%B%"` will select anything that contains a B somewhere. 
      * `"B%A"` selects antyhing that starts with B and ends with A
      * `"_B%"` where `_` is a single character wildcard. this will search for anything where the 2nd character is B
      * `LIKE concat('%', name, '%')` will store `name` as a variable and concat the comparison to comapre it to `"%[name]%"`
    * `XOR` is like an "or" comparison that takes 1 or the other but not both
    * `<>` is th not equal comaprison operator
    * `DISTINCT` only shows 1 row and elimates all duplicate rows
### Update a user's name (the Update operation in CRUD) 
  * `UPDATE users
SET full_name="Boris H"
WHERE username="_DreamLead";`
### Delete a user (the Delete operation in CRUD)
  * `DELETE FROM users
WHERE username="_DreamLead";`

## relational db
A relational database is a type of database that organizes data into tables, and links them, based on defined relationships. These relationships enable you to retrieve and combine data from one or more tables with a single query.

## tables
- Fields should only contain one value
- Duplicates are problematic because it makes the CRUD operations more challenging. For example, it would take longer to retrieve data because time would be wasted going through duplicate rows. Also, updating data would be an issue
- The step of removing repetitive data across columns the first normal form (1NF).
- The step of removing repetitive data across rows the second normal form (1NF).

## primary and foreign keys
- The way to draw links between tables is to first give each row in a table a unique identifier, termed a primary key, and then reference (foreign key) that primary key in the other table to which you want to link.
- A primary key should uniquely identify each row
- If a table already uses one of tis columns as a foreign key its best not to touch it and just create another column with id’s
- A primary key can be defined on more than one column
- This entire process is called normalization and its output is data that is cleanly organized according to the relational model. The consequence of this organization is that rows will appear in the database only once moving forward, which in turn make the CRUD operations easier.

## Entity-Relationship Diagrams
* [watch youtube video](https://www.youtube.com/watch?v=-fQ-bRllhXc&feature=emb_logo)
- To better understand how the tables in a relational database are connected to each other, we can use an ERD, or Entity Relationship Diagram. This is a kind of diagram that shows each table as a box. It links those boxes together indicating what kind of relationship they have with each other, such as one-to-many or one-to-one.
### Entity
* represents a person, place or thing that you want to track in a database (this is turned into a table). each row is an entity instance
### atrribute
*  describes various characteristics about an indivdual entity (the columns in a table)
### Primary/keys identifier
* an attribute or group of attributes that uniquley identifies an instance of the entity.
### relationship
* describes how one or more entites interact with each other (a verb is often used to describe the relationship)
### cardinality
* the count of insatnces that are allowed or are necessary between entity relationships
  * minumum cardinality: the minium instances allowed
  * maximum cardinality: the maximum insatnces allowed
  * crows foot notation:
    1. ----||-      (one mandatory)
    1. -----|E      (many mandatory)
    1. ----O|-      (one - optional)
    1. ----O|E      (many - optional)
  * you cannont have 2 tables connected both with a many link, if thats the case oyu need to have a middle table to connect these 2 tables  