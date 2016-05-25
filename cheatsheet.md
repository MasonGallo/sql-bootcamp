# SQL Cheatsheet

Keep this open throughout class!

## General SQL structure

```sql
SELECT <columns>
FROM <table>
[INNER|LEFT|RIGHT|FULL OUTER] JOIN <otherTable>
ON <table.key> = <otherTable.key>
WHERE <condition>
GROUP BY <columns>
HAVING <condition>
ORDER BY <columns> [DESC|ASC]
LIMIT <number>
```

## Using comments to make notes for yourself or others

`--` for single line comments

`/* blah
blah */` for multiline comments

## Creating, using, altering, deleting

- Create a new database named testbd

```sql
DROP DATABASE IF EXISTS testdb;
CREATE DATABASE testdb
```

- Tell SQL to use the testdb

```sql
USE testdb
```

- Create a table called users

```sql
CREATE TABLE users
(
user_id INT NOT NULL AUTO_INCREMENT,
first_name VARCHAR(20) NOT NULL,
last_name VARCHAR(30) NOT NULL,
age INT NOT NULL,
PRIMARY KEY (user_id)
);
```

- Add a column called something to the table users that is "hi" by default

```sql
ALTER TABLE users
ADD something VARCHAR(25) default "hi"
```

- Rename the something column to quite_something

```sql
ALTER TABLE users
CHANGE something quite_something VARCHAR(25)
```

- Delete the table users

```sql
DROP TABLE users
```



