### Easy leetcode challenge ###
#### 2021-10-05 ####
---------------------
**175. Combine Two Tables**
```sql
SELECT  t1.FirstName,
        t1.LastName,
        t2.City,
        t2.State
FROM    Person t1
LEFT JOIN   Address t2
ON          t1.PersonID = t2.PersonID
```

**176. Second Highest Salary**
```sql
#solution 1#
SELECT
    (SELECT DISTINCT
            Salary
        FROM
            Employee
        ORDER BY Salary DESC
        LIMIT 1 OFFSET 1) AS SecondHighestSalary
;

#solution 2#
SELECT MAX(Salary)
FROM  Employee 
WHERE Salary <
  (SELECT MAX(Salary)
   FROM   Employee )
   
#solution 3#
SELECT
IFNULL((SELECT  DISTINCT Salary 
FROM    Employee
ORDER BY    Salary DESC
LIMIT 1 OFFSET 1),null)AS SecondHighestSalary
```
---------------
