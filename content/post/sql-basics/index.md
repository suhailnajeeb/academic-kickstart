---
title: SQL Fundamentals (Part 1/3)
Date: 2020-04-13
authors:
- admin
Draft: true

---

While recently learning the basics of SQL, I created a bunch of notes for reference. You will find that these notes are parallel to the following online courses:

- [SQL and Relational Databases 101](https://cognitiveclass.ai/courses/learn-sql-relational-databases)
- [Databases and SQL for Data Science](https://www.coursera.org/learn/sql-data-science)

The course on [cognitiveclass.ai](https://cognitiveclass.ai) is free and  you could follow the materials if you want. The coursera course is part of coursera's
[IBM Data Science Professional Certificate]() Program and provides a brief introduction to SQL for data science.

The following examples aren't really descriptive if that is something you are looking for. Its mostly a collection of the basic syntaxes with some examples. Part 1 contains a summary of the following topics:

- Creating Tables:
    - CREATE statement
- Queries:
    - SELECT statement
    - WHERE clause
- Useful functions for query-ing:
    - 

## 5 Basic SQL Commands: 

* Create
* Insert
* Select
* Update
* Delete

## These commands are divided into 2 types:

* DDL Statements (Data Definition Language)
    * Define, Change or Drop Data
* DML Statements (Data Manipulation Language)
    * Read and Modify Data

# Creating Tables:

## Syntax:

```sql
create table TABLENAME (
    COLUMN1 datatype,
    COLUMN2 datatype,
    COLUMN3 datatype,
        ...
    ) ;
```
## Examples:

Varchar - Variable Character
```sql
create table TEST (
    ID integer,
    NAME varchar(30)
    );
```

Char-Fixed Character
```sql
create table COUNTRY (
    ID int,
    CCODE char(2),
    NAME varchar(60)
    );
```

Setting the Primary Key to ID
```sql
create table COUNTRY (
    ID int NOT NULL,
    CCODE char(2),
    NAME varchar(60),
    PRIMARY KEY (ID)
    );
```

Droping and creating table:
```sql
drop table COUNTRY;
create table COUNTRY (
    ID integer PRIMARY KEY NOT NULL,
    CCODE char(2),
    NAME varchar(60)
    );
```

# Select Statement:

Used for: 

* Retreiving Data from the Table.
* This is a DML Statement
* Select Statement: Query
* Result of Select: Result Set/Table

## Syntax:

```sql
select * from <tablename>
```

```sql
select COLUMN1, COLUMN2, ... from TABLE1;
```

## Example:
```
select ID, NAME from COUNTRY;
```

Retrieve all columns:

```sql
select * from country;
```

### Predicates:
- Search conditions
- Used in the search condition for the WHERE clause

WHERE Clause comparison objects:

```
=   Equal
>   Greater than
<   Less than
>=  Greater than or equal
<=  Less than or equal
<>  Not equal
```

## Examples:

```sql
select * from COUNTRY where ID <5;
```

```sql
select * from COUNTRY where CCODE = 'CA';
```

# Count Function:

Built-in function that retrieves the number of rows matching the query criteria.

## Examples:

Number of rows in the table:

```sql
select COUNT(*) from tablename;
```
Rows in MEDALS table where the country is Canada

```sql
select COUNT(*) from MEDALS
    where COUNTRY = 'CANADA';
```

# Distinct Function:

Used to Remove duplicate values in a result set.

## Syntax:

Retrieve Unique values in a column:
```sql
select DISTINCT columnname from tablename
```
## Example:

List of unique Countries that received GOLD medals.
```sql
select DISTINCT COUNTRY from MEDALS
    where MEDALTYPE = 'GOLD';
```

# Limit:

Restrict the number of rows retrieved from the database.

## Syntax:

Retrieve first 10 rows in a table:

```sql
select * from tablename LIMIT 10
```
## Example:

Retrieve 5 rows in the MEDALS table for the year 2018
```sql
select * from MEDALS
    where YEAR = 2018 limit 5
```

# Insert Statement: 

* Used for populating a table.
* DML Statement

## Syntax:

```sql
INSERT INTO tablename
    (Columnname,...,...)
    VALUES
    (Value,...,...,...)
```

## Example:

```sql
INSERT INTO AUTHOR
    (AUTHOR_ID, LASTNAME, FIRSTNAME, EMAIL, CITY, COUNTRY)
    VALUES
    ('A1', 'CHONG', 'RAUL', 'RFC@ABC.COM', 'TORONTO', 'CA');
```

Multiple entries: 

```sql
INSERT INTO AUTHOR
    (AUTHOR_ID, LASTNAME, FIRSTNAME, EMAIL, CITY, COUNTRY)
    VALUES
    ('A1', 'CHONG', 'RAUL', 'RFC@ABC.COM', 'TORONTO', 'CA'),
    ('A2', 'DHONG', 'BAUL', 'BFD@ABC.COM', 'TORONTO', 'CA');
```

# Update Statement:

- alter the data
- DML Statement

## Syntax:

```sql
UPDATE tablename
    SET columnname = value
    WHERE condition
```

## Example:

```sql
UPDATE AUTHOR
    SET LASTNAME = NAJEEB
        FIRSTNAME = SUHAIL
    WHERE AUTHOR_ID = 2
```

# Delete Statement:

- Remove rows from the Table

## Syntax:

```sql
DELETE FROM tablename
    WHERE condition
```
## Examples:
```sql
DELETE FROM AUTHOR
    WHERE AUTHOR_ID IN('A2','A3')
```