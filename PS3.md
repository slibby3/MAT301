## Problem Set 3 

1.Define the terms: relation, tuple, attribute, record, and field.

```
Relation - a table consisting of a set of tuples that can change over time
Tuple - rows of a relation with one component for each attribute
Attribute - table columns
Record - row of a table/relation
Field - column
```

2.What are keys in a relation?

`
Keys in a relation are one or more attribute used to identify a record. Keys can be unique or nonunique, but unique is prefered.
`

3.What is a surrogate key and how is it used?

`
A surrogate key is a column made by an arbitary assignment of a key to a row. It can be an auto-incremented integer that has no meaning - this tends to be used in cases where private data is not prefered. It can serve as a way to ID individuals without using social security numbers, for example.
`

4.In the following equation, Area = Length x Width, identify the determinant(s).

`
Length and width are the determinants.
`

5.If a relation has no duplicate data, how can you be sure there is always at least one primary key?

`

`

6.Give an example of a relation.  Determine a natural key for this relation.

`
...
`

  For question 7 - 8, Consider product *orders*.  In particular, associated with an order is: customer name (first and last), address (street, city, state, zip), phone, email, the products orders (including item, quantity, and price).  

7.Create a relational data model for *orders*.  Consider applying normalization rules (discuss Monday)

`
Customer
------------
| Cust_ID (PK) | Auto_increment
|---|
| Cust_First  |  
| Cust_Last | 
| Street_Ad | 
| Zip (FK) |
| Phone |
| Email |

Zip
------------
| Zip (PK) | 
|---|
| City  |  
| State | 

Products
------------
| Prod_ID (PK) | 
|---|
| Prod_name  |  
| Prod_price | 

Order Table
------------
| Prod_ID (PK) |
| Cust_ID (PK) |
|---|
| Quantity |  

`

8.For customer, could email be used as a primary key?  If so, state why.  Also, if possible to use as a primary key, discuss any disadvantages of using email as a primary key.

`
The email could be a primary key because it uniquely identifies an individual. The disadvantage would be that email can change over time (natural key) and may become an orphaned record. 
`

9.Given two relations S and R below find the Cartsian Product S x R. 

```
1,2,3,1,1
2,3,3,1,1
1,2,2,2,3
2,3,2,2,3
1,2,2,1,5
2,3,2,1,5
```

10.Find the natural join between the Faculty and Department relations below.

`
The natural join between the Faculty and Departmnet relations is the "Dept" column. "Dept" is a primary key in the Department relation and a foreign key in the Faculty relation. 
`


S
--------------
| A | B |
|---|---|
| 1 | 2 |
| 2 | 3 |
---------

R
------------
| C | D | E |
|---|---|---|
| 3 | 1 | 1 |
| 2 | 2 | 3 |
| 2 | 1 | 5 |



Faculty
--------------
| Name | ID | Dept |
|-------|----|----------------|
| Joe | 1 | Chemistry |
| Susan | 2 | Math |
| Tom | 3 | Marine Science |
| Mike | 4 | Math |


Department
------------
| Dept | Chair  |
|---|---|
| Chemistry | John |
| Math | Mike |
| Marine Science | Barry |
