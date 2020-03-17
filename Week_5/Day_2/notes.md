## W5 - D2

* [TEACHER NOTES](https://github.com/FrancisBourgouin/lectures-2020-mtl-feb03/tree/master/w5d2)
* [LECTURE RECORDING](https://www.youtube.com/watch?v=4HeN56P_05M&feature=youtu.be)

## TABLE DEFAULT VALUES
* when creating a table you can set default values example
```sql
CREATE TABLE teachers (
  id SERIAL PRIMARY KEY NOT NULL,
  name VARCHAR(255) NOT NULL,
  is_active BOOLEAN DEFAULT TRUE,
  start_date DATE,
  end_date DATE
);
```

## ERD (entity-relationship model)
* [lighthouse labs reference to create erd](https://web.compass.lighthouselabs.ca/activities/944)
* use pen and paper and after use the software [draw.io](https://www.draw.io/) to finalize it
* ERD is just a map so no need to include data types
* when making ERDs have user stories already made so that you know what your DB needs
* design process:
1. Determine the purpose of the database - This helps prepare for the remaining steps.
2. Find and organize the information required - Gather all of the types of information to record in the database, such as product name and order number.
3. Divide the information into tables - Divide information items into major entities or subjects, such as Products or Orders. Each subject then becomes a table.
4. Turn information items into columns - Decide what information needs to be stored in each table. Each item becomes a field, and is displayed as a column in the table. For example, an Employees table might include fields such as Last Name and Hire Date.
5. Specify primary keys - Choose each table's primary key. The primary key is a column, or a set of columns, that is used to uniquely identify each row. An example might be Product ID or Order ID.
6. Set up the table relationships - Look at each table and decide how the data in one table is related to the data in other tables. Add fields to tables or create new tables to clarify the relationships, as necessary.
7. Refine the design - Analyze the design for errors. Create tables and add a few records of sample data. Check if results come from the tables as expected. Make adjustments to the design, as needed.
8. Apply the normalization rules - Apply the data normalization rules to see if tables are structured correctly. Make adjustments to the tables, as needed.

## normalization
* The process of normalization organizes the data in a way that reduces redundancy. This makes the data highly space-efficient on disk, however it can have trade-offs (performance issues) when retrieving (quering) large sets of related data because it has to join/search/filter through many tables.
* the reason behind normalizing our data is: To enforce data integrity reduce duplication, and make it easier to manage our data.

## primary/foreign key
* A foreign key is a field in one table that refers to a primary key in another table. Foreign keys are how we model relationships in a relational database. 
* When we have a one-to-many relationship, the foreign key goes on the many side. So when a cohort has many students, the foreign key goes on the students side.
```js
       MANY                            ONE
+-----------------+            +-----------------+
|     students    |            |     cohorts     |
+-----------------+            +-----------------+
| PK | id         |       /----| PK | id         |
|    | name       |      /     |    | name       |
|    | email      |\    /      |    | start_date |
| FK | cohort_id  |----/       |    | end_date   |
|    | start_date |/           +-----------------+
|    | end_date   |
+-----------------+
```

## bridge tables
* when 2 (a and b) tables have a many-to-many realtionship you'll likely need to create a bridge table (c) that connects the 2.
* (a)----E(c)3-----(b)
* the naming convention for c's table title is a comboination of table title a and b. so if a was "author" and b was "title", c would be called "author_titles" 
* these tables usually have 1PK and 2FK