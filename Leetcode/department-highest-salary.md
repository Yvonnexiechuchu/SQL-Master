

### Question link: https://leetcode.com/problems/department-highest-salary/ ###
#### 2020-01-07 ####
**Answers**
```sql
SELECT  D.Name as Department,
        E.Name as Employee,
        E.Salary
FROM    Employee E
JOIN    Department D
ON      D.Id=E.DepartmentId
JOIN    (SELECT DepartmentId,
                MAX(Salary) as maxs
         FROM   Employee
         Group by 1) Temp
ON      D.Id=Temp.DepartmentId
WHERE   E.Salary= Temp.maxs
```

**Highlight**
#### 1. there might be 2 different employees who share the same salary and happen to be the highest, `order by limit 1` will not work

