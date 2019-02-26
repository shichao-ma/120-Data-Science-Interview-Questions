## Programming (14 questions)

#### 1. Write a function to calculate all possible assignment vectors of 2n users, where n users are assigned to group 0 (control), and n users are assigned to group 1 (treatment).
  - Recursive programming (sol in code)
#### 2. Given a list of tweets, determine the top 10 most used hashtags.
  - Store all the hashtags in a dictionary and get the top 10 values
  - heap
#### 3. Program an algorithm to find the best approximate solution to the knapsack problem1 in a given time.
  - Greedy solution (add the best v/w as much as possible and move on to the next)
#### 4. Program an algorithm to find the best approximate solution to the travelling salesman problem2 in a given time.
  - Greedy
#### 5. You have a stream of data coming in of size n, but you don’t know what n is ahead of time. Write an algorithm that will take a random sample of k elements. Can you write one that takes O(k) space?
  - https://en.wikipedia.org/wiki/Reservoir_sampling

#### 6. Write an algorithm that can calculate the square root of a number.
  - <https://www.quora.com/What-is-the-method-to-calculate-a-square-root-by-hand?redirected_qid=664405>
  - https://en.wikipedia.org/wiki/Newton's_method#Square_root_of_a_number
#### 7. Given a list of numbers, can you return the outliers?
  - sort then select the highest and the lowest 2.5%
  - compute variance and select those who fall outside of 2 or 3 sigma
#### 8. When can parallelism make your algorithms run faster?
  - When one job does not depend on the previous result.
  - Communication cost < computation cost
  - Some use cases
    - ensemble trees
    - minibatch
    - cross validation
    - forward propagation
  - not suitable for online learning

#### 9. What are the different types of joins? What are the differences between them?
  - (INNER) JOIN: Returns records that have matching values in both tables
  - LEFT (OUTER) JOIN: Return all records from the left table, and the matched records from the right table
  - RIGHT (OUTER) JOIN: Return all records from the right table, and the matched records from the left table
  - FULL (OUTER) JOIN: Return all records when there is a match in either left or right table

#### 10. Why might a join on a subquery be slow? How might you speed it up?
  - Too many rows.
  - Filter results using subqueries whenever possible.
  - Put WHERE condition into JOIN ON whenever possible.
#### 11. Describe the difference between primary keys and foreign keys in a SQL database.
  - Primary keys are columns whose value combinations must be unique in a specific table so that each row can be referenced uniquely. Foreign keys are columns that references columns (often primary keys) in other tables.
#### 12. Given a COURSES table with columns course_id and course_name, a FACULTY table with columns faculty_id and faculty_name, and a COURSE_FACULTY table with columns faculty_id and course_id, how would you return a list of faculty who teach a course given the name of a course?
~~~
SELECT 
    faculty_name 
FROM 
    FACULTY AS f 
JOIN
    COURSE_FACULTY AS cf
ON
    f.faculty_id = cf.faculty_id
JOIN
    COURSES AS c
ON
    cf.course_id = c.course_id
WHERE
    c.course_name = 'xxx';    
~~~
#### 13. Given a IMPRESSIONS table with ad_id, click (an indicator that the ad was clicked), and date, write a SQL query that will tell me the click-through-rate of each ad by month.
~~~
SELECT 
    ad_id, DATE_TRUNC('month', date) AS month, AVG(click) AS click-through-rate
FROM 
    IMPRESSIONS 
GROUP BY 1, 2;
~~~
#### 14. Write a query that returns the name of each department and a count of the number of employees in each:  
EMPLOYEES containing: Emp_ID (Primary key) and Emp_Name  
EMPLOYEE_DEPT containing: Emp_ID (Foreign key) and Dept_ID (Foreign key)  
DEPTS containing: Dept_ID (Primary key) and Dept_Name

~~~
SELECT 
    a.Dept_Name, COALESCE(COUNT(b.Emp_ID), 0)
FROM 
    DEPTS AS a 
LEFT JOIN 
    EMPLOYEE_DEPT AS b 
ON a.Dept_ID = b.Dept_ID 
GROUP BY 1;
~~~
