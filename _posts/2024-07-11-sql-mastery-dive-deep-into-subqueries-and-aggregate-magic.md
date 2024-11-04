---
title: "SQL Mastery: Dive Deep into Subqueries and Aggregate Magic"
excerpt: In this blog post, we’ll explore two powerful features of SQL subqueries and aggregate functions. Subqueries, or nested queries, allow you to build dynamic and sophisticated queries by embedding one query within another..
date: July 11, 2024
layout: post
author: neha
categories:
    - sql
image: assets/techalgospotlight-sql-banner.webp
keywords: sql
published: true
---

In this blog post, we’ll explore two powerful features of SQL: subqueries and aggregate functions. Subqueries, or nested queries, allow you to build dynamic and sophisticated queries by embedding one query within another. This technique is invaluable for filtering, transforming, and comparing data sets in nuanced ways. On the other hand, aggregate functions enable you to perform calculations on multiple rows and return a single summarizing value, such as totals, averages, counts, and more.

GROUP BY Clause
---------------

Till now we combined multiple values into a single value by doing some operation on all of them. What if, we want to get the final values in multiple sets? That is, we want to get the set of values as our result in which each value is derived from a group of values from the column.

The way the Group By clause works is it allows us to break the table into multiple groups so as to be used by the aggregate function.

For example: **GROUP BY batch_id** will bring all rows with the same **batch_id** together in one group

> Note: Also, GROUP BY always works before aggregate functions. Group By is used to apply aggregate function within groups (collection of rows). The result comes out to be a set of values where each value is derived from its corresponding group.

Let’s take an example.

![](https://techalgospotlight.com/wp-content/uploads/2024/07/image-11.png)

```sql
SELECT COUNT(*), batch_id FROM students GROUP BY batch_id;
```


The result of the above query will be:

![](https://techalgospotlight.com/wp-content/uploads/2024/07/image-12.png)

Explanation: The query breaks the table into 3 groups each having rows with **batch_id** as 1, 2, 3 respectively. There are 4 rows with **batch_id = 1**, 3 rows with **batch_id = 2** and 2 rows with **batch_id = 3**.

Note that, we can only use the columns in SELECT which are present in Group By because only those columns will have the same value across all rows in a group.

#### **Ordering of Operations:**

```txt
1. Select the tables. 
  1.2. Do the joins if required
  
2. Apply the filters (where clause) 

3. Group by 
   3.2: Filtering happens with having clause 

4. Select what to print including aggregates

5. Order by, limit, offset. 
```

* * *

### Aggregate Examples

##### Q1: Print the name of every actor (first\_name, last\_name) and with that print the number of films they have acted in.

```sql
SELECT
    a.first_name, a.last_name, count(1) AS count_movies

  FROM actor a
    JOIN film_actor b
       ON a.actor_id = b.actor_id
  
       
GROUP BY a.actor_id
```

##### Q2: If you have a table `user_classes` with columns as (userID, classID, attended (0 / 1)), then find user-wise attendance.

```sql
SELECT userid, AVG(attended) FROM user_classes GROUP BY userid
```

* * *

##### Q: Find the number of rounds given by every user in every company they interviewed for.

```sql
SELECT user_id, company_id, count(1)
FROM companies_users 
GROUP BY user_id, company_id
```

* * *

HAVING Clause
-------------

The HAVING clause is used to filter groups. Let’s take a question to understand the need for a HAVING clause:

There are 2 tables: Students(id, name, age, batch\_id) and Batches(id, name). Print the batch names that have more than 100 students along with a count of the students in each batch.

```sql
SELECT COUNT(S.id), B.name
FROM Students S
JOIN Batches B ON S.batch_id = B.id
GROUP BY B.name;
HAVING COUNT(S.id) > 100;
```


Here, **GROUP BY B.name** group the results by the **B.name** column (batch name). It ensures that the count is calculated for each distinct batch name. **HAVING COUNT(S.id) > 100** condition filters the grouped results based on the count of **S.id** (number of students). It retains only the groups where the count is greater than 100.

The sequence in which the query executes is:

*   Firstly, join of the two tables is done.
*   Then it is divided into groups based on **B.name**.
*   In the third step, the result is filtered using the condition in the HAVING clause.
*   Lastly, it is printed through SELECT.

FROM -> WHERE -> GROUP BY -> HAVING -> SELECT

WHERE is not built to be able to handle aggregates. We can not use WHERE after GROUP BY because the WHERE clause works on rows and as soon as GROUP BY forms a result, the rows are converted into groups. So, no individual conditions or actions can be performed on rows after GROUP BY.

* * *

Imagine you are given an employee table which has all employee ID, names and their salary. If I asked you to report employees who earn more than the company average, how would you do it?

Note that the following query does not work:

```sql
SELECT * FROM employees WHERE salary > AVG(salary)
```

**Why?**: Because where clause filters row by row. Aggregation only happens at the time of printing (unless for group\_by and having clause). WHERE clause does not know about AVG(salary).

Manually, I will first find out the company average and then put it in a query. But what if I did not want to put it manually? Subqueries come to our rescue here.

If I break the above down, what are the steps:

*   Step 1: Find the average salary amongst all employees.

```sql
SELECT AVG(salary) FROM employees
```

*   Step 2: Find all employees who make more than the above number.

```sql
SELECT * FROM employees WHERE salary > (SELECT AVG(salary) FROM employees)
```

As you can see, in SQL, it’s possible to place an SQL query inside another query. This inner query is known as a subquery. In a subquery, the outer query’s result depends on the result set of the inner subquery. That’s why subqueries are also called nested queries.

### Subqueries Examples

##### Q: Find all employees who make more salary than their department average.

What’s step 1 here? I need to find out department-wise average salaries. Ok, let’s do that.

```sql
SELECT dept, AVG(salary) FROM employees GROUP BY dept
```

If the above was a table, would it be possible to get results quickly by doing a JOIN? Oh yes, absolutely. Let’s do that then.

```sql
SELECT
  e.id, e.name
FROM employees AS e
  JOIN (SELECT dept, AVG(salary) AS dept_salary FROM employees GROUP BY dept) AS tmp_table
  ON (e.dept = tmp_table.dept AND e.salary > tmp_table.dept_salary)
```

Hope this helps build intuition about the group by, having sub-queries.