
### Medium leetcode challenge ###
#### 2021-10-12 ####
---------------------
**177. Nth Highest Salary**
```sql
SELECT  DISTINCT  t1.Salary from
      (
          SELECT   Salary, DENSE_Rank() over(ORDER BY salary DESC) rk
          FROM      Employee 
          ) t1
      WHERE rk = N
```
use dense_Rank function
```sql
dense_rank over (partition by order by DESC)
```
----------------

**178. Rank Scores**
```sql
SELECT S.Score,
        DENSE_Rank() over(ORDER BY S.Score DESC) AS 'rank'
FROM    Scores S
ORDER BY S.Score desc
```

**180. Consecutive Numbers**
```sql
SELECT DISTINCT a.num as ConsecutiveNums
from Logs a
inner join Logs b
on a.Id + 1 = b.Id and a.Num = b.Num
inner join Logs c
on a.Id+2 = c.Id and a. Num = c.Num
 ```
 use inner join to find out consecutive relationship between different rows
