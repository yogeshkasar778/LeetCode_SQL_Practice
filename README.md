# :computer: LeetCode SQL Question and Answer - 
- [Easy](https://github.com/yogeshkasar778/StrataScratch_SQL_Practice#dart-difficulty-level---easy)
  
##  :dart: `Difficulty Level - Easy`
  
 ### Q.1 Write a solution to find the ids of products that are both low-fat and recyclable. Return the result table in any order.
 
   `Table Name - Product`
  
  playbook_events-
  
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













    
