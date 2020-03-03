# w5 - d1

## types of databases
1. relational
2. non-relational (MONGO, COUCH, FIREBASE)

## style convention
* the convention for naming columns in a DB is SNAKE_CASE
* capitalize the SQL keywords

## null value in sql
* for targetting rows that have a value of null (empty data) in the `WHERE` clause use `IS NULL` or `IS NOT NULL` for the opposite

## postgreSQL
* to enter database type: `psql` in the terminal
* to exit type: `\q`
* to create a db type: `CREATE DATABASE [name-of-db];`
* after createion to enter into it type: `\c [name-of-db]`
* `\l` (lowercase L) to see all databases on the server
* `\dt` to show all tables in current connected DB
* `\d [tableName]` will show you what that tbale looks liek with all columns and data types

## inserting already-made files as data
* create fake data in external .sql file
* inside a psql session in terminal type: `\i [file-location]`

## joining tables for a query
```sql
SELECT students.name as student_name, email, cohorts.name as cohort_name
FROM students JOIN cohorts ON cohort_id = cohorts.id;
```
* <strong>every join must hav an `ON`</strong>
### inner join
* An INNER JOIN will only give us rows where there is a match between the two tables. Any students with a cohort_id of NULL will not appear in the results of this kind of join.
### outer join
* there are 3 categories in outer join:
  1. LEFT: favors the table thats wirtten in `FROM` and will show all those rsults regardless of a match
  2. RIGHT: favors the table thats written in `JOIN` and will show all those results regardless of a match
  3. FULL: will return everything even when there is no match
* the full query for an outer join is:
```sql
FROM students LEFT OUTER JOIN cohorts ON cohorts.id = cohort_id;
```
* When we write a LEFT OUTER JOIN or a RIGHT OUTER JOIN, we can omit the word OUTER, therefore:
```sql
FROM students LEFT JOIN cohorts ON cohorts.id = cohort_id;
```
* summary:
  * In this exercise we learned about two different types of joins, INNER and OUTER.

  * An INNER JOIN will only return results where there is a match between the two tables.

  * An OUTER JOIN will do the same as an INNER JOIN but also returns unmatched rows in one or both tables. An OUTER JOIN can be LEFT, RIGHT, or FULL.

  * Inner join produces only the set of records that match in both Table A and Table B.

  * Full outer join produces the set of all records in Table A and Table B, with matching records from both sides where available. If there is no match, the missing side will contain null.

  * Left outer join produces a complete set of records from Table A, with the matching records (where available) in Table B. If there is no match, the right side will contain null.

## having
* The HAVING clause is like WHERE but works on aggregated data. Our WHERE clause works on normal data `students.end_date` and our HAVING clause works on the aggregated data `count(assignment_submissions.*)`

## SQL ORDER
1. SELECT
2. FROM
3. JOIN
4. WHERE
5. GROUP BY
6. HAVING
7. ORDER BY

## nesting select queries
* If a query returns a single value, we can use it in our SELECT statement just like any other value.

```sql
SELECT (
  SELECT count(assignments)
  FROM assignments
)-count(assignment_submissions)
```

```sql
SELECT 424-count(assignment_submissions)
```

* the query `SELECT count(assignments)
  FROM assignments` will return 424 but instead of hardcoding it (in case this value will change in the future) we can nest it inside a select

## nesting where clauses
* If the result of a query returns only one column, we can use that sub query in our WHERE clause.

```sql
SELECT assignments.name
FROM assignments 
WHERE id NOT IN
(
  SELECT assignment_id
  FROM assignment_submissions
  JOIN students ON students.id = student_id
  WHERE students.name = 'Ibrahim Schimmel'
);
```
```sql
SELECT assignment_id
  FROM assignment_submissions
  JOIN students ON students.id = student_id
  WHERE students.name = 'Ibrahim Schimmel'
```
* the 2nd snippet returns a single column with data (1, 2, 3, 4, 5, 6 ...) so because of that we can levrage the `IN` clause and nest this select query for the `IN` clause to verify if the id is in that list

## GROUP BY
* when using an aggregate function like `COUNT` you need to have a `GROUP BY`

## limit 
* `LIMIT 2 OFFSET 0` = 1ST PAGE WITH 2 RESULTS (1 and 2)
* `LIMIT 2 OFFSET 2` = 2ND PAGE WITH 2 RESULTS (3 AND 4)