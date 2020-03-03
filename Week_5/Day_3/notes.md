# w5- d3

## DATA DEFINITION LANGUAGE (ddl)
* the sql commands that we use to define the database schema are somtimes referred to as data definition langauge
* the most common DDL statements are 
1. `create` (create)
2. `alter` (modify)
3. `drop` (remove)
.. objects sucha as tables/indexes/users

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