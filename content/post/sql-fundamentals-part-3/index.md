---
title: SQL Fundamentals (Part 3/3)
Date: 2020-04-25
authors:
- admin
Draft: true
tags: ["SQL", "Data", "Databases"]

---

<figure>
    <img src="/img/sql/database.jpg">
    <a href = "https://www.pexels.com/photo/bandwidth-close-up-computer-connection-1148820/" target = "_blank">
    <figcaption>Photo by Panumas Nikhomkhai from Pexels</figcaption>
    </a>
</figure>

---

This is the Part 3 of my SQL Fundamentals series, continuing from [Part 2](/post/sql-fundamentals-part-2) where I discussed about matching string patterns, Ranges, Sets, Sorting, Grouping, Filtering etc. Part 3 of this series covers the following topics:

- Functions in SQL:
    - Aggregate/Column Functions: SUM, MIN, MAX, AVG
    - Scalar and String Functinos: ROUND, LENGTH, UCASE, DCASE
    - Date-Time Functions
- Sub-Queries and Nested Selects
- Working with Multiple Tables etc.

The following statemetns aren't really descriptive if that is something you are looking for. Its mostly a collection of the basic syntaxes with some examples. This is the [link](https://github.com/suhailnajeeb/learning-sql) to the corresponding github repository. You will find some relevant example sql queries in the [Problems](https://github.com/suhailnajeeb/learning-sql/tree/master/problems) folder of the repository.

---

# Functions in SQL:

- Built-in Functions
- User Defined Functions

# Aggregate or Column Functions

## Sum Function: 

Add up all values in a column

## Syntax:

```sql
SUM(COLUMN_NAME)
```

## Examples:

Add all values in the SALEPRICE column

```sql
select SUM(SALEPRICE) from PETSALE
```
Explicitly name the output column SUM_OF_SALEPRICE

```sql
select SUM(SALEPRICE) as SUM_OF_SALEPRICE
    from PETSALE
```

# MIN, MAX, AVG

## Min: Returns the minimum value

```sql
select MIN(ID) from PETSALE where ANIMAL = 'Dog'
```

## Max: Returns the maximum value

```sql
select MAX(QUANTITY) from PETSALE
```

## Average: Return the average value

```sql
select AVG(SALEPRICE) from PETSALE
```

Mathematical operations can be performed between columns

```sql
select AVG(SALEPRICE / QUANTITY) from PETSALE
    where ANIMAL = 'Dog'
```

# Scaler and String Functions

## ROUND()

Round up or down every value in saleprice:

```sql
select ROUND(SALEPRICE) from PETSALE
```
Retrieve the length of each value in ANIMAL:

## LENGTH()

```sql
select LENGTH(ANIMAL) from PETSALE
```

## UCASE

Retrieve ANIMAL values in Uppercase:

```sql
select UCASE(ANIMAL) from PETSALE
```

## DCASE

```sql
select * from PETSALE
    where LCASE(ANIMAL) = 'cat'
```
select distinct values:

```sql
select DISTINCT(UCASE(ANIMAL)) from PETSALE
```

# Date, Time Functions

## Examples:

Extract the DAY portion from a date:

```sql
select DAY(SALEDATE) from PETSALE
    where ANIMAL = 'Cat'
```

Get the number of sales during the month of May:

```sql
select COUNT(*) from PETSALE
    where MONTH(SALEDATE) = '05'
```

## Date/Time Arithmetic:

What date is it 3 days after each sale date? 

```sql
select (SALEDATE + 3 DAYS) from PETSALE
```
Special Registers:

```sql
CURRENT_DATE, CURRENT_TIME
```
Find how many days have passed since each SALEDATE till now:

```sql
select (CURRENT_DATE - SALEDATE) from PETSALE
```

# Sub-Queries and Nested Selects:

## Sub-Query:

A Query inside another Query

```sql
select COLUMN1 from TABLE
    where COLUMN2 = (select MAX(COLUMN2) from TABLE)
```

## Example: 

Retrieve the list of employees who earn more than the average salary:

**THIS IS INCORRECT**

```sql
select * from employees
    where salary > AVG(salary)
```

**You cannot aggregate functions like AVG() in the WHERE clause**

*Solution*: Use a sub-select expression.

```sql
select EMP_ID, F_NAME, L_NAME, SALARY
    from employees
    where salary >
    (select AVG(SALARY) from employees);
```
## Sub-Queries in list of columns

- Substitute column name with a sub-query
- Called Column Expressions

**THIS IS INCORRECT**
```sql
select EMP_ID, SALARY, AVG(SALARY) AS AVG_SALARY
    from employees;
```

```sql
select EMP_ID, SALARY,
    ( select AVG(SALARY) from employees)
        AS AVG_SALARY
    from employees;
```

## Sub-queries in FROM Clause

- Substitute the TABLE name with a sub-query
- These are called Derived Tables or Table Expressions

```sql
select * from
    ( select EMP_ID, F_NAME, L_NAME, DEP_ID
        from employees) AS EMP4ALL;
```

# Working With Multiple Tables:

Ways to access multiple tables in the same query:

1. Sub-queries
2. Implicit JOIN
3. JOIN operators (INNER JOIN, OUTER JOIN, etc.)

## Accessing Multiple Tables with Sub-queries:

Retrieve only the employee recrds that correspond to departmetns in the DEPARTMENTS table:

```sql
select * from employees
    where DEP_ID IN
        (select DEPT_ID_DEP from departments);
```

Retrieve only the list of employees from a specific location:
- EMPLOYEES table does not contain location information
- Need to get location info from DEPARTMENTS table

```sql
select * from employees
    where DEP_ID_IN
        (select DEPT_ID_DEP from departments
            where LOC_ID = 'L0002');
```

Retreive department ID and name for employees who earn more than $70,000

```sql
select DEPT_ID_DEP, DEP_NAME from departments
    where DEPT_ID_DEP IN
        (select DEP_ID from employees
            wehre SALARY > 70000)
```

## Accessing Multiple Tables with Implicit Join:

Specify 2 Tables in the FROM clause:

```sql
select * from employees, departments;
```

The result is a full join (Cartesian Join)
- Every row in the first table is joined with every row in the 2nd table

Limiting the result set: 

```sql
select * from employees, departments
    where employees.DEP_ID = 
        departments.DEPT_ID_DEP;
```

Using shorter aliases for table names:

```sql
select * from employees E, departments D
    where E.DEP_ID = D.DEPT_ID_DEP;
```

See the department name for each employee:

```sql
select employees.EMP_ID, departments.DEPT_NAME
    from employees E, departments D
    where E.DEP_ID = D.DEPT_ID_DEP;
```

Column names can be pre-fixed by aliases also:

```sql
select E.EMP_ID, D.DEPT_NAME
    from employees E, departments D
    where E.DEP_ID = D.DEPT_ID_DEP;
```

You can find some relevant SQL queries [here](https://github.com/suhailnajeeb/learning-sql/blob/master/problems/problemset_2.sql).

- [Link](/post/sql-fundamentals-part-1) to **Part 1**
- [Link](/post/sql-fundamentals-part-2) to **Part 2**

*This post ends this SQL Fundamentals series. I hope that you have found it helpful. Thank you for sticking till the end!*