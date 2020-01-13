### Question link: https://www.hackerrank.com/challenges/sql-projects/problem ###
#### 2020-01-12 ####
**Answers**
```sql
SET sql_mode='';
SELECT  Start_Date,
        min(End_Date)
FROM
(
SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects))A,
(SELECT End_Date FROM Projects WHERE End_Date NOT IN (SELECT Start_Date FROM Projects))B

WHERE   Start_Date<End_Date
GROUP BY    Start_Date
ORDER BY DATEDIFF(End_Date, Start_Date), Start_Date
```

**Highlight**
#### 1. For the Date to be used with `Group by` clause, it should either be mentioned in `Group by` Clause or Aggregate function. Here, `Group by` is used on `start_date`. So, `end_date` needs to be added in aggregate function. You can use MIN or MAX for it.

#### 
