# w5- d3

* [teacher notes](https://github.com/FrancisBourgouin/lectures-2020-mtl-feb03/tree/master/w5d3)
* [lecture video part 1](https://www.youtube.com/watch?v=IzsGF-zqOXc&feature=youtu.be)
* [lecture video part 2](https://www.youtube.com/watch?v=Kjdx7KIPsl8&feature=youtu.be)

## QUICK TABLE GUIDE LHL
* REFERENCE FOR SETTING UP A TABLE (SCROLL DOWN TO BOTTOM FOR QUICK RFERENCE) [LINK](https://web.compass.lighthouselabs.ca/days/w05d3/activities/952)

## DATA DEFINITION LANGUAGE (DDL)
* the sql commands that we use to define the database schema are somtimes referred to as data definition langauge
* the most common DDL statements are 
1. `create` (create)
2. `alter` (modify)
3. `drop` (remove)
.. objects sucha as tables/indexes/users

## DATA MANIPULATION LANGAUGE (DML)
* sql commands that elt us interact with our data are sometimes called DATA MANIPUALTION LANGUAGE (DML). these includes:
  1. `select`: get data from tables
  2. `insert`: add rows to a table [read more](https://www.tutorialspoint.com/sql/sql-insert-query.htm)
  3. `update`: update rows within a table [read more](https://www.tutorialspoint.com/sql/sql-update-query.htm)
  4. `delete`: delete rows from a table [read more](https://www.tutorialspoint.com/sql/sql-delete-query.htm)

### INSERT
* insert has 2 syntaxes
1. `INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (1, 'Ramesh', 32, 'Ahmedabad', 2000.00 );`
* in this one you specficy the columns and then you insert values keeping the same order
2. `INSERT INTO CUSTOMERS 
VALUES (7, 'Muffy', 24, 'Indore', 10000.00 );`
* in this one you just write the values in order of how your table's columns. this only works if youre adding data for ALL the columns of your table

### UPDATE
* modify existing records. use a WHERE clause otherwise all rows will be affected
* syntax:
``` sql
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];
```
* you can use `AND` or `OR` in the `WHERE` clause
* syntax withotu a `WHERE` clause `UPDATE CUSTOMERS
SET ADDRESS = 'Pune', SALARY = 1000.00;`

### DELETE
* you probably shoudl specify  a `WHERE` clause otherwise all the records will eb deleted
* the syntax is:
``` sql
DELETE FROM table_name
WHERE [condition];
```
* you can combine `AND` or `OR` in the `WHERE` clause
* if you want to delete all the records there is no need to specify a `WHERE` clause. syntax: `DELETE FROM CUSTOMERS;`

## data types in PSTGRESQL
* all [data types](https://www.postgresql.org/docs/9.3/datatype.html) in `pqsl` 

### character data types
* `CHAR(n)` is the fixed-length character with space padded. If you insert a string that is shorter than the length of the column, PostgreSQL pads spaces. If you insert a string that is longer than the length of the column, PostgreSQL will issue an error.
* `VARCHAR(n)` is the variable-length character string.  With VARCHAR(n),  you can store up to n characters. PostgreSQL does not pad spaces when the stored string is shorter than the length of the column.
* `TEXT` is the variable-length character string. Theoretically, text data is a character string with unlimited length.

### integer
* Small integer `SMALLINT` is 2-byte signed integer that has a range from -32,768 to 32,767.
* Integer `INT` is a 4-byte integer that has a range from -2,147,483,648 to 2,147,483,647.
* Serial is the same as integer except that PostgreSQL will automatically generate and populate values into the `SERIAL` column. This is similar to `AUTO_INCREMENT` column in MySQL or `AUTOINCREMENT` column in SQLite.

### temporal (time)
* `DATE` stores the dates only.
* `TIME` stores the time of day values.
* `TIMESTAMP` stores both date and time values.
* `TIMESTAMPTZ` is a timezone-aware timestamp data type. It is the abbreviation for timestamp with the time zone.
* `INTERVAL` stores periods of time.

### UUID (UNIVERSAL UNIQUE ID)
* The UUID data type allows you to store Universal Unique Identifiers defined by RFC 4122 . The UUID values guarantee a better uniqueness than SERIAL and can be used to hide sensitive data exposed to the public such as values of id in URL.

## ALTERING AN EXISTING TABLE
* [THE DOCS](https://www.postgresqltutorial.com/postgresql-alter-table/)
* GENERAL SYNTAX
```SQL
ALTER TABLE table_name action;
```
``` sql
ALTER TABLE users ADD COLUMN name VARCHAR(255); 
```

## DROPPING A TABLE
* `DROP TABLE IF EXISTS [tableName] CASCADE;`
* deletes all data
* cascade will make sure that all records from other tables that depend on this table will also be deleted.
* And to avoid any SQL errors, it's good to make sure the table exists before dropping it.

## HOW TO MAKE A NODE APP TO QUERY SQL
```js
const { Pool } = require('pg');

const pool = new Pool({
  user: 'vagrant',
  password: '123',
  host: 'localhost',
  database: 'bootcampx'
});

let userInput = process.argv.slice(2);

pool.query(`SELECT DISTINCT teachers.name AS teacher,
cohorts.name AS cohort
FROM assistance_requests
  JOIN teachers ON teachers.id = assistance_requests.teacher_id
  JOIN students ON students.id = assistance_requests.student_id
  JOIN cohorts ON cohorts.id = students.cohort_id
WHERE cohorts.name = '${userInput[0]}'
ORDER BY teachers.name`)
.then(res => {
  res.rows.forEach(row => {
    console.log(`${row.cohort}: ${row.teacher}`);
  })
});
```