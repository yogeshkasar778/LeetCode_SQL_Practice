# :computer: LeetCode SQL Question and Answer - 
- [Easy](https://github.com/yogeshkasar778/StrataScratch_SQL_Practice#dart-difficulty-level---easy)
  
##  :dart: `Difficulty Level - Easy`
  
 ### Q.1 Write a solution to find the ids of products that are both low-fat and recyclable. Return the result table in any order.
 
   `Table Name - Product`
   
| Column Name | Type |
| ----------- | ---  |
| product_id  | int  |
| low_fats    | enum |
| recyclable  | enum |

product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

The result format is in the following example.

**Example 1:** 

**Input:**

Products table:
| product_id   | low_fats  | recyclable  |
| ----------- | ---------  | ----------  |
|      0      |  Y  | N |
|      1      |  Y  | Y |
|      2      |  N  | Y |
|      3      |  Y  | Y |
|      4      |  N  | N |

 ###  Solution - 
    
    SELECT product_id 
    FROM Product
    WHERE low_fats = 'Y' AND recyclable = 'N';

**Output:**

| product_id |
|----------- |
| 1 |
| 3 |

 ### Q.2 Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.
 
   `Table Name - Customer `
  
| Column Name | Type | 
| ----------- | ---  |
| id          | int  |
| name        | varchar |
| referee_id    | int |

In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

The result format is in the following example.

**Example 1:** 

**Input:**

Customer table:
| id    | name   | referee_id   |
| ----------- | ---------  | ----------  |
|      1      |  Will   | null        |
|      2      |  Jane   | null        |
|      3      |  Alex   | 2           |
|      4      |  Bill   | null        |
|      5      |  Zack   | 1           |
|      6      |  Mark   |  2          |
 ###  Solution - 
    
    SELECT name 
    FROM Customer
    WHERE referee_id <> 2 AND referee_id is null;

**Output:**

| name |
|----------- |
| Will  |
| Jane  |
| Bill  |
| Zack  |

 ### Q.3 A country is big if: it has an area of at least three million (i.e., 3000000 km2), or it has a population of at least twenty-five million (i.e., 25000000). Write a solution to find the name, population, and area of the big countries. Return the result table in any order.
 
   `Table Name - World `
  
| Column Name | Type | 
| ----------- | ---  |
| name        | int  |
| continent   | varchar |
| area     | int |
|population| int |
| gdp |  bigint  |

name is the primary key (column with unique values) for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.

The result format is in the following example.

**Example 1:** 

**Input:**

World table:
| name    | continent   | area   | population | gdp |
| ----------- | ---------  | ----------  | ---| ---|
|   Afghanistan       |  Asia         | 652230          |25500100   |20343000000  |
|      Albania           |  Europe       | 28748           |2831741    |12960000000  |
|      Algeria           |  Africa       | 2381741            |37100000   |188681000000 |
|      Andorra           |  Europe       | 468             |78115      |3712000000   |
|      Angola            |  Africa       | 1246700            |20609294   |100990000000 |

 ###  Solution - 
    
    SELECT name, population, area 
    FROM World
    WHERE area >= 3000000 or population >= 25000000;

**Output:**

| name | population | area |
|----------- |------|------|
| Afghanistan   |25500100   |652230  |
| Algeria       |37100000   |2381741 |

 ### Q.4 Write a solution to find all the authors that viewed at least one of their own articles. Return the result table sorted by id in ascending order.
 
   `Table Name - Views `
  
| Column Name | Type | 
| ----------- | ---  |
| article_id            | int  |
| author_id        | int |
| viewer_id          | int |
|view_date     | date |

There is no primary key (column with unique values) for this table, the table may have duplicate rows.
Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.

The result format is in the following example.

**Example 1:** 

**Input:**

Views table:
| article_id     | author_id    | viewer_id    | view_date   | 
| ----------- | ---------  | ----------  | --- |
|   1       |  3         | 5          |2019-08-01   |
|      1           |  3       | 6           |2019-08-02    |
|      2           |  7       | 7            |2019-08-01   |
|      2           |  7       | 6             |2019-08-02       |
|      4            |  7       | 1            |2019-07-22   |
|      3            |  4       | 4            |2019-07-21   |
|      3            |  4       | 4            |2019-07-21   |

 ###  Solution - 
    
    SELECT DISTINCT author_id as id 
    FROM Views
    WHERE author_id=viewer_id
    ORDER BY author_id;

**Output:**

| id | 
|----------- |
| 4   |
| 7       |

 ### Q.5 Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15. Return the result table in any order.
 
   `Table Name - Tweets `
  
| Column Name | Type | 
| ----------- | ---  |
| tweet_id      | int  |
| content        | varchar |

tweet_id is the primary key (column with unique values) for this table.
This table contains all the tweets in a social media app.

The result format is in the following example.

**Example 1:** 

**Input:**

Tweets table:
| tweet_id    | content    | 
| ----------- | ---------  | 
|   1         |  Vote for Biden   | 
|      2      |  Let us make America great again!  | 


 ###  Solution - 
    
    SELECT tweet_id 
    FROM Tweets
    WHERE len(content)>15;

**Output:**

| tweet_id | 
|----------- |
| 2   |

 ### Q.6 Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null. Return the result table in any order.
 
   `Table Name - Employees `
  
| Column Name | Type | 
| ----------- | ---  |
| id      | int  |
| name        | varchar |

id is the primary key (column with unique values) for this table.
Each row of this table contains the id and the name of an employee in a company.

   `Table Name - EmployeeUNI `
  
| Column Name | Type | 
| ----------- | ---  |
| id      | int  |
| unique_id             | int |

(id, unique_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.

The result format is in the following example.

**Example 1:** 

**Input:**

Employees  table:
| id    | name    | 
| ----------- | ---------  | 
|   1         | Alice      | 
|      7      |  Bob       | 
|      11     |  Meir      | 
|      90     | Winston   |
|      3      | Jonathan   | 

EmployeeUNI   table:
| id     | unique_id     | 
| -----------| ---------| 
|   3        | 1         | 
|      11    |  2       | 
|      90    | 3        |


 ###  Solution - 
    
    SELECT eU.unique_id, e.name 
    FROM Employee as e
    LEFT JOIN EmployeeUNI as eU ON e.id=eU.id;

**Output:**

| unique_id | name     |
|-----------|----------|
| null      |Alice     |
| null      |Bob       |
| 2         |Meir      |
| 3         |Winston   |
| 1         |Jonathan  |

 ### Q.7 Write a solution to report the product_name, year, and price for each sale_id in the Sales table. Return the resulting table in any order.
 
   `Table Name - Sales `
  
| Column Name | Type | 
| ----------- | ---  |
| sale_id           | int  |
| product_id          | int |
| year                  | int |
| quantity              | int |
| price                 | int |

(sale_id, year) is the primary key (combination of columns with unique values) of this table.
product_id is a foreign key (reference column) to Product table.
Each row of this table shows a sale on the product product_id in a certain year.
Note that the price is per unit.

   `Table Name - Product `
  
| Column Name | Type | 
| ----------- | ---  |
| product_id         | int  |
| product_name              | varchar |

product_id is the primary key (column with unique values) of this table.
Each row of this table indicates the product name of each product.

The result format is in the following example.

**Example 1:** 

**Input:**

Sales   table:
| sale_id      | product_id      | year |quantity |price |
| -----------| ---------| ---|--|--|
|   1        | 100         |2008 |10|5000|
|      2    |  100       | 2009|12|5000|
|      3    | 200        |2011|15|9000|

Product  table:

| product_id       | product_name       | 
| -----------| ---------| 
|   1        | 100       |
|      2    |  100       | 
|      3    | 200        |

 ###  Solution - 
    
    SELECT eU.unique_id, e.name 
    FROM Employee as e
    LEFT JOIN EmployeeUNI as eU ON e.id=eU.id;

**Output:**

| unique_id | name     |
|-----------|----------|
| null      |Alice     |
| null      |Bob       |
| 2         |Meir      |
| 3         |Winston   |
| 1         |Jonathan  |










    
