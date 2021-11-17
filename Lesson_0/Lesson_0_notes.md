## Lesson 0 Notes

### SQL

<u>Overview</u></br>
--------------------
[Basic Query](#basic_query)</br>
[WHERE Clause](#where)</br>
[= (EQUALS)](#equal)</br>
[AND operator](#and)</br>
[<> (NOT EQUAL)](#not_equal)</br>

Sample Table **Person**
```
_________________________________________
|ID | First Name | Surname | DOB        |
----------------------------------------
| 0 |Bob        | Brown   | 1970-01-20  |
-----------------------------------------
```
<a id="basic_query">All basic Data Manipulation Language (DML) queries are of this basic structure.</a>


```
SELECT 'First Name', Surname, DOB
FROM Person
```


We are feeling really lazy and as we want to get all the columns from the table we can use the `*` operator

```
SELECT *
FROM Person
```

We just want to see people's first names.

When we choose a subset of columns using SQL, that is called Projection. This term comes from relational algebra.

```
SELECT 'First Name'
FROM Person
```

<a id="where">Imagine you only want to find people with the first name Bob. Well in that case, let's introduce the `WHERE` clause</a>

When we choose a subset of rows using SQL, that is called Selection, this also comes from relational algebra. But Selection corresponds with `WHERE` **NOT** `SELECT`

<a id="equal">Because we want to find all people with a first name equal to 'Bob' we use equal sign `=`</a>

```
SELECT 'First Name', Surname, DOB
FROM Person
WHERE 'First Name' = 'Bob'
```

<a id="and">You don't want to see any people named Smith in addition to people being named Bob so we link these together with `AND`</a>

<a id="not_equal"> Not equal is  `<>`</a

```
SELECT 'First Name', Surname, DOB
FROM Person
WHERE 'First Name' = 'Bob' AND Surname <> 'Smith'
```

Let's say we have another table named Cat_Ownership_Summary (which was derived from another table - see this later)

Table Cat_Ownership_Summary

ID | NumCats
0  | 2

We want to see the person's id and number of cats who own more than 2 cats. We can use the greater than sign, `>`
```
SELECT ID, NumCats
FROM Cat_Ownership_Summary
WHERE NumCats > 2;
```

A strange person wants to see people who own 1 cat, 4 cats and 7 cats. We can use `IN` keyword
```
SELECT ID, NumCats
FROM Cat_Ownership_Summary
WHERE NumCats IN (1, 4, 7);
```

Someone believes that the right number of cats is between 3 and 6. We can use the `BETWEEN` keyword
```
SELECT ID, NumCats
FROM Cat_Ownership_Summary
WHERE NumCats BETWEEN 3 AND 6;
```

This could also be expressed less concisely as
```
SELECT ID, NumCats
FROM Cat_Ownership_Summary
WHERE NumCats >= 3 AND NumCats <= 6;
```

A person named Zara created a 'Z' day on the 2nd February. They want to find all people with a given name starting with 'Z' so they can celebrate Z day together.
We can use the operator `LIKE` with the string operator `%` to represent 1 or more wildcard characters.
```
SELECT 'First Name', Surname, DOB
FROM Person
WHERE 'First Name' LIKE 'Z%'
```

