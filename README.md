# SQL (Structured Query Languange)

- Language via which you can create,update and delete data in database

## Database management Systems 

- Software via which you can interect with database
  Ex:
  - MySQL
  - Oracle
  - PostgreSQL
  - SQLite
  - 
## Querying

- Ask questions about data
  
  "" used for column names
  '' for string names
  It is good practice to use double quotes around table and column names, which are called SQL identifiers. SQL also has strings and we use single quotes around strings to differentiate them from identifiers.


  ###   SELECT allows us to select some (or all) rows from a table inside the database.

  ```
  SELECT "something" FROM  "table-name";
  ```


  **SELECT ALL**
  ```
  SELECT *
  FROM "longlist";
  ```

  **SELECT ONE table**
    ```
  SELECT "title"
  FROM "longlist";
  ```

  **SELECT MULTIPLE**
  ```
  SELECT "title", "author"
  FROM "longlist";
  ```

### LIMIT 

- Limit the number of items within 

```
  SELECT "title" FROM "longlist" LIMIT 10;

```
- in this case the first 10;
- WHERE is used to select rows based on a condition; it will output the rows for which the specified condition is true.

### WHERE

- get rolls where the condition is true

 ```
 SELECT "title", "author" FROM "longlist" WHERE "year" = 2013;
 ```
 ```
  SELECT "title", "author" FROM "longlist" WHERE "year" = 2013 OR "year"=2024;
 ```
```
SELECT "title", "author" FROM "longlist" WHERE ("year" = 2013 OR "year"=2024) and "format" !='hardcover';
```

 ```
SELECT "title", "format" 
FROM "longlist" 
WHERE "format" != 'hardcover';
 ```


### = equal
```
SELECT "title", "author" 
FROM "longlist" 
WHERE "year" = 2023;
```

### != not equal
```
SELECT "title", "format" 
FROM "longlist" 
WHERE "format" != 'hardcover';
```
###  <> not equal
```
SELECT "title", "format" 
FROM "longlist" 
WHERE "format" <> 'hardcover';
```
###  NOT  not equal

```
SELECT "title", "format" 
FROM "longlist" 
WHERE NOT "format" = 'hardcover';
```

AND
OR
() first or after 

```
SELECT "title", "format" 
FROM "longlist" 
WHERE ("year" = 2022 OR "year" = 2023) AND "format" != 'hardcover';
```

### NULL

IS NULL
IS NOT NULL

- value isn't on the data base

To select the books for which translators don’t exist, we can run

```
SELECT "title", "translator" 
FROM "longlist"
 WHERE "translator" IS NULL;
```
Let’s try the reverse: selecting the books for which translators do exist.

```
SELECT "title", "translator" 
FROM "longlist"
WHERE "translator" IS NOT NULL;
```
### LIKE

roughly matches the specified string

To select the books with the word “love” in their titles, we can run

```
SELECT "title"
FROM "longlist"
WHERE "title" LIKE '%love%';
```

To select the books whose title begin with “The”, we can run
```
SELECT "title" 
FROM "longlist" 
WHERE "title" LIKE 'The%';
```
To select only the books whose titles begin with the word “The”, we can add a space.
```
SELECT "title" 
FROM "longlist" 
WHERE "title" LIKE 'The %';
```

Book in the table whose name is either “Pyre” or “Pire”, we can select it by running
```
SELECT "title" 
FROM "longlist" 
WHERE "title" LIKE 'P_re';
```
_ matches any single character.

### range conditions 

>=
<=
>
<
BETWEEN ... AND ...

  ```
  SELECT "title", "author" FROM "longlist"  WHERE "year" >=2019 AND "year" <= 2022;
  SELECT "title", "author" FROM "longlist"  WHERE "year" BETWEEN 2019 AND 2022;
  SELECT "title" , "rating", "votes FROM "longlist" WHERE "rating" > 4.0 AND "votes" > 10000;

  ```
### ORDER BY

- ORDER BY .. ASC
- ORDER BY ... DESC

```
SELECT "title", "rating" FROM "longlist" ORDER BY "rating" LIMIT 10;
SELECT "title", "rating", "votes" FROM "longlist" ORDER BY "rating" DESC, "votes" DESC LIMIT 10;

```

Sort alphabetically

```
SELECT "title",  FROM "longlist" ORDER BY "title";
```

### aggregaate functions 

To find the average rating of all books in the database
```
SELECT AVG("rating") 
FROM "longlist";
```
To round the average rating to 2 decimal points
```
SELECT ROUND(AVG("rating"), 2) 
FROM "longlist";
```
To rename the column in which the results are displayed
```
SELECT ROUND(AVG("rating"), 2) AS "average rating" 
FROM "longlist";
```
Note the use of the SQL keyword AS to rename columns.

To select the maximum rating in the database
```
SELECT MAX("rating") 
FROM "longlist";
```
To select the minimum rating in the database
```
SELECT MIN("rating") 
FROM "longlist";
```
To count the total number of votes in the database
```
SELECT SUM("votes") 
FROM "longlist";
```
To count the number of books in our database
```
 SELECT COUNT(*) 
 FROM "longlist";
```
Remember that we used * to select every row and column from the database. In this case, we are trying to count every row in the database and hence we use the *.
To count the number of translators
```
SELECT COUNT("translator") 
FROM "longlist";
```
We observe that the number of translators is fewer than the number of rows in the database. This is because the COUNT function does not count NULL values.
To count the number of publishers in the database
```
SELECT COUNT("publisher") 
FROM "longlist";
```
As with translators, this query will count the number of publisher values that are not NULL. However, this may include duplicates. Another SQL keyword, DISTINCT, can be used to ensure that only distinct values are counted.
```
SELECT COUNT(DISTINCT "publisher") 
FROM "longlist";
```
