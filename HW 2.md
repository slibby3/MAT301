### Problem Set 2 - Query Writing (continued)
---



#### Column Aliases

Often column names are obfuscated which make query's output difficult to understand. 
**Column Aliases** is a "nickname" (or *alias*) for a table's column(s) that gives a more user friendly (descriptive) name.
To give a column an alias, use the `AS` keyword followed by the alias name.  For example:

```SQL
SELECT product_id AS itemcode FROM Products;
```

If the alias contains space, use quotes.  

```SQL
SELECT product_id AS `item code` FROM Products;
```

NOTE: The alias does not permenantly rename the column and is only temporary assignment.




---

#### SQL operators

---

Operators are reserved words used with the `WHERE` clause to perform an operation such as comparisons.  The primary operators are:

- Comparison operators (e.g., equality)
- Logical operators (including negation)
- Conjunctive operators
- Arithmetic operators

##### Comparison operators

Comparison operators include equality, non-equality, less than, and greater than.  The equal sign is used to test equality.  For example, 

```SQL
SELECT product_id FROM Products WHERE product_id=2000;
```
One way to select all product_id's not equal to 2000 is the following SELECT statement 

```SQL
SELECT product_id FROM Products WHERE product_id<>2000;
```
---

###### Less than (and greater than)

And example using less than, (greater than is similar), which will return all product id's that cost less than $10:

```SQL
SELECT product_id FROM Products WHERE price<10;
```

###### Less than or equal

Combining the operators can give more specific results.  For example, SELECT all product id's less than or equal to $10.


```SQL
SELECT product_id FROM Products WHERE price<=10;
```

---

##### Logical Operators

Logical operators include `IS NULL`, `BETWEEN`, `IN`, `LIKE`, `EXISTS`, `UNIQUE`, `ALL`, `SOME`, and `ANY`.
Logical operators are used (mostly) with the `WHERE` clause.  

The following queries serve as examples for the LOGICAL operators.


```SQL
SELECT * FROM Products WHERE price IS NULL;
```


```SQL
SELECT * FROM Products WHERE price BETWEEN 10 and 20;
```


```SQL
SELECT * FROM Products WHERE price IN(9.99, 19.99, 29.99);
```

The `LIKE` operator returns similar values using *wildcards* (underscore _ and percent %).  The underscore represents one character where as the percent represents multiple characters.

The following returns all rows where the country starts with a letter 'C'.  

```SQL
SELECT * FROM Products WHERE country like 'C%';
```

The following returns all rows where the price ends in a 9.


```SQL
SELECT * FROM Products WHERE price like '%9';
```

The following returns rows where price has any value for the tens place and a 9 in the ones (pennies):


```SQL
SELECT * FROM Products WHERE price like '%._9';
```

#### Conjunctive operators (AND and OR)

Conjunctions are used to make more complex queries.  For example suppose we want all products whose price is greater than 10 but less than 20.  The following will return the desired results:

```SQL
SELECT * FROM Products WHERE price>10 AND price<20;
```

Two ways to write the query to return products with price less than or equal to $20:


```SQL
SELECT * FROM Products WHERE price<=20;
```


```SQL
SELECT * FROM Products WHERE price<20 OR price=20;
```

#### Negation

Equality is negated using `!=` or `<>`.  All other statements can be negated using `NOT` operator. 



#### Arithmetic operators

Arithmetic operators (`+`, `-`, `*`, `/`) can be used to perform calculations on the results of columns.  It is good to alias results of using arithmetic operators.  For example, 


```SQL
SELECT 1.35*price AS `Sale Price` FROM Products;
```




#### Exercises


===

***` Cost = 'price', price = msrp `***

1.Select all products (UPC) made in China whose price is less than $50.

```SQL
SELECT upc
FROM unemath_Libby.Products
WHERE country='China'
AND msrp<'50';
```

2.Find products with "bird bath" in the description.

```SQL
SELECT name, description
FROM unemath_Libby.Products
WHERE description LIKE 'bird bath%';
```

3.Find products whose cost is between $10 and $100.

```SQL
SELECT product_id, price
FROM unemath_Libby.Products
WHERE price BETWEEN 10 and 100;
```

4.Find products whose cost is less than or equal to $59.99.

```SQL
SELECT *
FROM unemath_Libby.Products
WHERE price<='59.99';
```

5.Find products whose ID is between 5000 and 6000 or 7483, 4939, 3452, 9848, 11293, 12001.

```SQL
SELECT name, product_id
FROM unemath_Libby.Products
WHERE product_id BETWEEN 5000 and 6000
OR product_id IN(7483,4939,3452,9848,11293,12001);
```

6.Find products that are not between 5000 and 6000 or 7483, 4939, 3452, 9848, 11293, 12001.

```SQL
SELECT name, product_id
FROM unemath_Libby.Products
WHERE product_id NOT BETWEEN 5000 and 6000
OR product_id NOT IN(7483,4939,3452,9848,11293,12001)
```

7.Find products whose country code is NULL.

```SQL
SELECT *
FROM unemath_Libby.Products
WHERE country IS NULL;
```

8.Calculuate the shipping volume and report it as 'Volume'.

```SQL
SELECT name, 
ROUND(ship_depth*ship_width*ship_length,2) 
AS volume
FROM unemath_Libby.Products
```

9.Suppose you want to have a 35% markup on all products and sales tax is 7.5%.  Determine the 'Sales Price' of each product.

```SQL
SELECT name, 
ROUND(1.75*1.35*price,2)
AS 'sales price'
FROM unemath_Libby.Products;
```

10.True or False: Both conditions when using the OR operator must be true.

***`False`***

11.What is the logical negation of the IN operator?

***`NOT is the negation of the IN operator`***

12.What is wrong with the folling statement: `SELECT * FROM Products WHERE price BETWEEN 10, 100;

***`Should be: SELECT * FROM Products WHERE price BETWEEN 10 AND 100`***

13.Select products with length less than 12 inches and sort decsending.

```SQL
SELECT name, length
FROM unemath_Libby.Products 
WHERE length<12
ORDER BY length DESC;
```

14.How many products are there whose price is between $10 and $20?

```SQL
SELECT COUNT(*)
FROM unemath_Libby.Products
WHERE price BETWEEN 10 AND 20;
```

***`3226 products`***

15.How many products are there made in China whose MSRP is between $10 and $20. 

```SQL
SELECT COUNT(*)
FROM unemath_Libby.Products
WHERE country='China'
AND msrp BETWEEN 10 AND 20;
```

***`2189 products`***
