---
title: SQL Fundamentals (Part 2/3)
Date: 2020-04-17
authors:
- admin
Draft: false
tags: ["SQL", "Data", "Databases"]

---

<figure>
    <img src="/img/sql/database.jpg">
    <a href = "https://www.pexels.com/photo/bandwidth-close-up-computer-connection-1148820/" target = "_blank">
    <figcaption>Photo by Panumas Nikhomkhai from Pexels</figcaption>
    </a>
</figure>

---

This is the Part 2 of my SQL Fundamentals series, continuing from [Part 1](/post/sql-fundamentals-part-1) where I discussed Creating Tables, Querying with SELECT and WHERE, introduced some useful functions like COUNT, DISTINCT, LIMIT and some DML statements - INSERT, UPDATE, DELETE Etc. Part 2 of this series covers the following topics:

- Matching String Patterns
- Ranges
- Sets
- Sorting
- Eliminating Duplicates
- Grouping, Counting
- Filtering Grouped results.

The following statemetns aren't really descriptive if that is something you are looking for. Its mostly a collection of the basic syntaxes with some examples. This is the [link](https://github.com/suhailnajeeb/learning-sql) to the corresponding github repository. You will find some relevant example sql queries in the [Problems](https://github.com/suhailnajeeb/learning-sql/tree/master/problems) folder of the repository.

---
# String Patterns

## Matching string:

```sql
select book_id, title from book
    where book_id = 'B1';
```

## Looking for String Patterns:

Display all authors with firstname starting with R  
**Predicate:** Like  
**Wildcard:** %

```sql
select firstname from author
    where firstname like 'R%';
```
---

# Ranges:

## Without Range:

```sql
select title, pages from book
    where pages >= 290 and pages <= 300;
```

## Retrieving values using Range:

```sql
select title, pages from book
    where pages between 290 and 300;
```
---

# Sets

## Without set of values:
```sql
select firstname, lastname, country from author
    where country = 'AU' or country = 'BR';
```

## Retrieving rows using a set of values:
```sql
select firstname, lastname, country from author
    where country in ('AU', 'BR');
```
---

# Sorting Result Sets:

## Order by title (Ascending Order):

```sql
select title from book
    order by title;
```

## Order by title (Descending Order):

```sql
select title from book
    order by title desc;
```

## Order by specifying the column number:

```sql
select title, pages from book
    order by 2;
```

## Distinct Clause: (Eliminating Duplicates)

List the unique countries:

```sql
select distinct(country) from author
```
---

# Count:

Counting the number of countries:

```sql
select country, count(country) from author
    group by country
```

Counting the number of countries and giving the count column a name: 

```sql
select country, count(country) as count
    from author
    group by country
```

## Having Clause:

Restricting the result set using **having** clause.

*Having clause is used with group-by clause only*

```sql
select country, count(country) as count
    from author
    group by country
    having count(country) > 4
```

---

You can find some relevant SQL queries [here](https://github.com/suhailnajeeb/learning-sql/blob/master/problems/problemset_2.sql).

- [Link](/post/sql-fundamentals-part-1) to **Part 1**
- [Link](/post/sql-fundamentals-part-3) to **Part 3**

*To be continued ..*