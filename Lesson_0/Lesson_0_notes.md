## Lesson 0 Notes

### SQL

Sample Table **Person**
```
_________________________________________
|ID | First Name | Surname | DOB        |
----------------------------------------
| 0 |Bob        | Brown   | 1970-01-20  |
-----------------------------------------
```
All basic Data Manipulation Language (DML) queries are of this basic structure.


```
SELECT 'First Name', Surname, DOB
FROM Person
```

Imagine you only want to find people with the first name Bob. Well in that case, let's introduce the `WHERE` clause

```
SELECT 'First Name', Surname, DOB
FROM Person
WHERE 'First Name' = 'Bob'
```

You don't want to see any people named Smith in addition to people being named Bob so we link these together with `AND`
```
SELECT 'First Name', Surname, DOB
FROM Person
WHERE 'First Name' = 'Bob' AND Surname <> 'Smith'
```

Let's say we have another table named Cat_Ownership_Summary (which was derived from another table - see this later)

Table Cat_Ownership_Summary

ID | NumCats
0  | 2

We want to see the person's id and number of cats who own more than 2 cats.
```
SELECT ID, NumCats
FROM Cat_Ownership_Summary
WHERE NumCats > 2;
```
