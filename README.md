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

  ###   SELECT = get something

  ```
  SELECT "something" FROM  "table-name";

  // SELECT ALL
  SELECT * FROM "longlist";

  //SELECT ONE
  SELECT "title" FROM "longlist";

  //SLECT MULTIPLE
  SELECT "title", "author" FROM "longlist";
  ```
### LIMIT 

- show the first limited numbers 

```
  SELECT "title" FROM "longlist" LIMIT 10;

```
- in this case the first 10;

### WHERE

- get rolls where the condition is true

 ```
  SELECT "title", "author" FROM "longlist" WHERE "year" = 2013;
  SELECT "title", "author" FROM "longlist" WHERE "year" = 2013 OR "year"=2024;
 SELECT "title", "author" FROM "longlist" WHERE ("year" = 2013 OR "year"=2024) and "format" !='hardcover';
```

= equal
!= not equal
<> not equal
AND
OR
() first or after 

### NULL

IS NULL
IS NOT NULL

- value isn't on the data base

 ```
 SELECT "title", "translator" FROM "longlist" WHERE "translatpr" IS NULL;
```

### LIKE

unlike = it's case incensitive aka doesn't matter 

% match any character around a string 
EX::
- '%tax%' could be 'higher tax etc'
- 'The%' only with "The" in the beginning 'The new etc' but also "their, they"
- 'The %'now will only show 'The' 


_ match any single character
Ex: 'P_re' will find pyre

can used multiple ___

  ```
  SELECT "title", "author" FROM "longlist"  WHERE "title" LIKE '%love%';
  ```

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

- COUNT
- AVG
- MIN
- MAX
- SUm
