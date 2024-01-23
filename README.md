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










    
