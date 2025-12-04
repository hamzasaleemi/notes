# Database Notes

## Database
Collection of data in a format that can be easily accessed.

## Types
* **Relational**: Data is stored in tables format for example MySQL, MS SQL, PostgreSQL.
* **Non-relational** or **NoSQL**: Data not stored in tables for example MongoDB.

## Database Management System
DBMS is an application used to manage database.

## SQL
Structed Query Language is used to interact with relational DBMS to get data from database.

## Types of SQL Commands
* DDL (Data Definition Language): create, alter, rename, truncate, drop columns or tables.
* DQL (Data Query Language): select data
* DML (Data Manipulation Language): insert, update, delete data.
* DCL (Data Control Language): grant and revoke permission to user.
* TCL (Transaction Control Language): start transaction, commit, rollback 

## SEQUEL
Structed English Query Language was created by IBM and then slowly the english part was removed and it changed to SQL.

## CRUD Operations:
* Create
* Read
* Update
* Delete

## Database Structure
Database contains interrelated tables which contains data.

## Table
Combination of columns and rows.

## Columns
Design of the table.

## Rows
Individual data.

## Keys
* **Primary Key**: A column or set of columns in a table that uniquely identify each row. There is only one primary key in a table and it cannot be NULL.
* **Foreign Key**: A column or set of columns in a table that refers to primary key of another table. Can have duplicate or NULL value.

## Cascading in Foreign Keys
* `ON DELETE CASCADE`: If primary table row is deleted it will delete the foreign key table row too.
* `ON UPDATE CASCADE`: If primary table row is updated it will update the foreign key table row too.

## Database Indexing
Lets suppose data is stored in pages and when we try to fetch data, memory have to iterate from page 1 and goes to the page where our result is that can be on page 1,000,000. So this will be costly for our performace. So we have a page of indexing where we store information of each page. Now after indexing memory will fetch that indexing page and will then fetch the exact page where our result is which will save us from iterating through each page.

## Indexing Types
* B-Tree: Binary tree structure indexing where pages are fetched applying by condition on column and fetching right or left node depending on the condition.
* Hash Index: Value is stored with a hash that directly points to the page where it exists.
* Geospatial: Used when dealing with longitude and latitudes map data.
    * Geohasing: A method in which we have layers like first layer is world map split into 4 parts and then each part will be more detailed layer. Most Popular.
    * QuadTrees: A method in which we split map into parts depending on a number k. So if a part contains more that k records it will split the part.
    * R-Tree: It used Minimum Bounding Rectangle. MBR is the smallest rectangle that completely encloses a given geometric object or a set of objects. R-trees allow MBRs of different nodes to overlap.
* Inverted Index: Used in searching text.

## Constraints
Used to specify rules for data in a table.
* `NOT NULL`: Cannot have a null value.
* `UNIQUE`: Value should be unique.
* `PRIMARY KEY`: Make column not null and unique.
* `FOREIGN KEY (column) REFERENCES table(column)`: Prevent actions that will destroy links between table.
* `DEFAULT`: Sets the default value of column.
* `CONSTRAINT <name> CHECK (<condition>)`: Limit the values allowed in a column.
* `AUTO_INCREMENT`: Auto increase value of ID and assign to new row.

## Database Commands
* `CREATE DATABASE IF NOT EXISTS db_name`: Create a new database if already not created.
* `DROP DATABASE IF EXISTS db_name`: Delete a database.
* `USE db_name`: Use the given database. This will allow to use tables without need to mention database name.
* `SHOW DATABASES`: List all databases.

## Table Commands
* `SHOW TABLES`: Show all tables.
* `CREATE TABLE <table> (<column> <datatype> <constraint>)`: Create a new table with given columns.
* `ALTER TABLE <table> RENAME TO <name>`: Rename existing table.

## Table Column Commands
* `ALTER TABLE <table> ADD COLUMN <column> <datatype> <constraint>`: Add a column to existing table.
* `ALTER TABLE <table> CHANGE COLUMN <column> <name> <datatype> <constraint>`: Update name, datatype and constraint of existing column in existing table.
* `ALTER TABLE <table> MODIFY COLUMN <column> <datatype> <constraint>`: Update datatype and constraint of existing column in existing table.
* `ALTER TABLE <table> DROP COLUMN <column>`: Delete a column from existing table.

## Table Rows Commands
* `INSERT INTO <table> (<column>) VALUES (value)`: Insert data in a table.
* `UPDATE <table> SET <column> = <value> WHERE <condition>`: Update column or columns values in a table.
* `DELETE FROM <table> WHERE <condition>`: Delete rows from table using a condition.
* `TRUNCATE TABLE <table>`: Delete all rows in a table.

## Fetch Data Commands
* `SELECT * FROM <table>`: Select all rows from table.
* `DISTINCT <column>`: Used to get unique values.
* `WHERE <condition>`: Used to apply condition for select statement.
* `GROUP BY <column>`: Group rows that have same values of one or more columns. Need to have same columns in select as in group by which do not have aggregate function.
* `HAVING`: Used to apply condition on data after group by.
* `ORDER BY <column> <order>`: Order the result in ASC or DESC order.
* `LIMIT (<offset>, <count>)`: Limit the number of rows from offset.

## Alias
`AS`: To give short name to table or column.

## Aggregate Functions
* `COUNT`: Number of rows.
* `MAX`: Maximum value in a row.
* `MIN`: Minimum value in a row.
* `SUM`: Sum of values of all rows.
* `AVG`: Average value of all rows.

## WHERE Operators
* Arithmetic Operators: +. -. *, %(modulus)
* Comparison Operators: =, !=, >, >=, <, <=
* Logical Operators: AND, OR, NOT, IN, BETWEEN, ALL, LIKE, ANY
* Bitwise Operators: &, |

## DataTypes
* `VARCHAR(size)`: A VARIABLE length string (can contain letters, numbers, and special characters). The size parameter specifies the maximum string length in characters - can be from 0 to 65535.
* `TEXT(size)`: Holds a string with a maximum length of 65,535 bytes.
* `ENUM(val1)`: A string object that can have only one value, chosen from a list of possible values. You can list up to 65535 values in an ENUM list. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them.
* `TINYINT(size)`: A very small integer. Signed range is from -128 to 127. Unsigned range is from 0 to 255. The size parameter specifies the maximum display width (which is 255).
* `INT(size)`: A medium integer. Signed range is from -2147483648 to 2147483647. Unsigned range is from 0 to 4294967295. The size parameter specifies the maximum display width (which is 255).
* `BIGINT(size)`: A large integer. Signed range is from -9223372036854775808 to 9223372036854775807. Unsigned range is from 0 to 18446744073709551615. The size parameter specifies the maximum display width (which is 255).
* `DECIMAL(size, d)`: An exact fixed-point number. The total number of digits is specified in size. The number of digits after the decimal point is specified in the d parameter. The maximum number for size is 65. The maximum number for d is 30. The default value for size is 10. The default value for d is 0.
* `DATETIME(fsp)`: A date and time combination. Format: YYYY-MM-DD hh:mm:ss. The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'. Adding DEFAULT and ON UPDATE in the column definition to get automatic initialization and updating to the current date and time.
* `DATE`: A date. Format: YYYY-MM-DD. The supported range is from '1000-01-01' to '9999-12-31'.
* `TIME(fsp)`: A time. Format: hh:mm:ss. The supported range is from '-838:59:59' to '838:59:59'
* `TIMESTAMP(fsp)`: A timestamp. TIMESTAMP values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:00' UTC). Format: YYYY-MM-DD hh:mm:ss. The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC. Automatic initialization and updating to the current date and time can be specified using DEFAULT CURRENT_TIMESTAMP and ON UPDATE CURRENT_TIMESTAMP in the column definition.
* `BOOLEAN`: Boolean values 0 or 1.
* `UNSIGNED`: Postive numeric datatype only.
* `SIGNED`: Postive and negative both numeric datatype.

## Joins
Used to combine rows from 2 or more tables based on related columns between them.

## Types of Join
* `INNER JOIN <table> ON <condition>`: Fetch intersection or common values of 2 tables.
* `LEFT JOIN <table> ON <condition>`: Fetch all values from first table.
* `RIGHT JOIN <table> ON <condition>`: Fetch all values from second table.
* `UNION`: Fetch all values from both tables. Give unique values only. So sort and compare is applied which effects performance.
* `UNION ALL`: Fetch all values from both tables. Give unique values.

## Views
It is a virtual table based on a result set of an SQL statement.

## View Commands
* `CREATE VIEW <name> AS SELECT <column> FROM <table>`: Create a view. After creating it can be used like SELECT * FROM <view>.
* `DROP VIEW <view>`: Delete a view.

## Stored Procedure
These are routines that contain a series of SQL statements and procedural logic.

## Stored Procedure Usage:
```
DELIMITER $$
CREATE PROCEDURE <name>(IN <arg> <datatype>, OUT <output> <datatype>)
BEGIN
    SELECT
        SUM(<column>) INTO <output>
    FROM
        <table>
    WHERE
        <column> = <arg>;
END$$
DELIMITER ;
```

## Functions
Set of SQL statements to get result. Use deterministic if we know the reuslt will be same for an input everytime.

## Functions Usage:
```
DELIMITER $$
CREATE FUNCTION <name>(<arg> <datatype>) RETURNS <datatype>
DETERMINISTIC
BEGIN
    DECLARE <result> <datatype>;
    SELECT
        SUM(<column>) INTO <result>
    FROM 
        <table>
    WHERE
        <column> = <arg>;
    RETURN <result>;
END$$
DELIMITER ;
```

## Transactions
A sequence of one or more SQL operations that are executed as a single unit of work. If all operations are successful then we commit changes to database else if any operation fails we will rollback changes to ensure data integrity.

## Transaction States
* **Active**: The initial state that means transaction is being executed and can perform read and write operations.
* **Partially Commited**: A state after performing final operation or query.
* **Commited**: A state where all operations are performed successfully and the effect of the transaction are now permanent in the database.
* **Failed**: If any of the transaction-related operations cause an error during the active or partially committed state, further execution of the transaction is stopped and it is brought into a failed state.
* **Aborted**: If a transaction reaches the failed state due to a failed check, the database recovery system will attempt to restore it to a consistent state. If recovery is not possible, the transaction is either rolled back or cancelled to ensure the database remains consistent.
* **Terminated**: It refers to the final state of a transaction, indicating that it has completed its execution. Once a transaction reaches this state, it has either been successfully committed or aborted.

## Transaction Commands
* `START TRANSACTION`: Start a transaction.
* `COMMIT`: Commit a transaction.
* `ROLLBACK`: To rollback the transaction.
* `SAVEPOINT`: Sets a savepoint within a transaction to rollback to later.

## ACID Properties
* **Atomicity**: All operations succeed or none do.
* **Consistency**: The database must remain in a valid state before and after the transaction.
* **Isolation**: Transaction occurs independantly without interference.
* **Durability**: Once commited, changes are permanent even if the system crash.

## Query Optimization
* `EXPLAIN`: Analyze a statement without executing and give estimate on how will query perform.
* `EXPLAIN FORMAT=JSON`: Analyze a statement and returns output as JSON string.
* `EXPLAIN ANALYZE`: Runs a statement and produces output which includes exectution cost, estimated number of returned rows, time to return first row, time spent executing the iterator, number of rows returned by iterator and number of loops.
* `SELECT` only required columns.
* Use `LIMIT` to implement pagination this will reduce dataset.
* Filter data using `WHERE` statment early to reduce dataset.
* **Indexing**: Use indexes on where, join and order by columns. Avoid indexing small tables. Over-indexing will slow down write operation performance.
* `JOIN` only neccessary tables.
* Don't use `WHERE` condition of joined table after `JOIN` becaue now extra rows are alreday joined.
* `DISTINCT` can be slow as it forces the database to sort and compare rows to remove duplicate. We can use `GROUP BY` instead.
* Select appropriate datatypes. Try to have smaller types.
* Use same datatype when using a condition like use id = 123 instead of id = '123'
* Use `UNION ALL` instead of `UNION` when you don't care about duplicates.
* Use Stored Procedures as they have already compiled queries.
* Avoid `!=` or `<>` in `WHERE` clause.
* Use `EXISTS` instead of `IN` as `IN` scans whole result but `EXISTS` stops on 1st match.
* Delete or Update huge dataset in batches like for 1,000,000 we can delete in 10,000 batches.
* Insert multiple at a time instead of one row at a time.
* Optimize LIKE searches. Apply Inverted indexing.

## EXPLAIN Output
* **id**: Select statement sequential number.
* **select_type**: The type of the select. We have following types:
    * **SIMPLE**: not using union or subqueries.
    * **PRIMARY**: Outermost select or main/first select.
    * **UNION**: Second or later select statement in a union.
    * **DEPENDENT UNION**: Second or later select statement in a union, dependent on outer query.
    * **UNION RESULT**: Result of a UNION.
    * **SUBQUERY**: First select in subquery.
    * **DEPENDENT SUBQUERY**: First select in subquery, dependent on outer query.
    * **DERIVED**: Derived table.
    * **DEPENDENT DERIVED**: Derived table dependent on another table.
    * **MATERIALIZED**: Materialized subquery.
    * **UNCACHEABLE SUBQUERY**: A subquery for which the result cannot be cached and must be re-evaluated for each row of the outer query.
    * **UNCACHEABLE UNION**: The second or later select in a UNION that belongs to an uncacheable subquery.
* **table**: The name of the table to which the row of output refers.
* **partitions**: The partitions from which records would be matched by the query. The value is NULL for nonpartitioned tables.
* **type**: The join type.
* **possible_keys**: The possible_keys column indicates the indexes from which MySQL can choose to find the rows in this table.
* **key**: The key column indicates the key (index) that MySQL actually decided to use. If MySQL decides to use one of the possible_keys indexes to look up rows, that index is listed as the key value.
* **key_len**: The key_len column indicates the length of the key that MySQL decided to use. The value of key_len enables you to determine how many parts of a multiple-part key MySQL actually uses. If the key column says NULL, the key_len column also says NULL.
* **ref**: The ref column shows which columns or constants are compared to the index named in the key column to select rows from the table.
* **rows**: The rows column indicates the number of rows MySQL believes it must examine to execute the query.
* **filtered**: The filtered column indicates an estimated percentage of table rows that are filtered by the table condition. The maximum value is 100, which means no filtering of rows occurred. Values decreasing from 100 indicate increasing amounts of filtering. rows shows the estimated number of rows examined and rows × filtered shows the number of rows that are joined with the following table. For example, if rows is 1000 and filtered is 50.00 (50%), the number of rows to be joined with the following table is 1000 × 50% = 500.
* **Extra**: This column contains additional information about how MySQL resolves the query.