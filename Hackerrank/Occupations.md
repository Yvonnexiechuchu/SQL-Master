
### Question link: https://www.hackerrank.com/challenges/occupations/problem ###
#### 2020-01-06 ####
**Answers**
```sql
set @rownum=0;
set @rownum1=0;
set @rownum2=0;
set @rownum3=0;
set @rownum4=0;
SELECT d.Name, p.Name, s.Name, a.Name from 
(SELECT @rownum:=@rownum+1 AS id FROM OCCUPATIONS order by Name) m
left JOIN (SELECT @rownum1:=@rownum1+1 AS id, Name FROM OCCUPATIONS where Occupation='Doctor' order by Name) d ON d.id = m.id
left JOIN (SELECT @rownum2:=@rownum2+1 AS id, Name FROM OCCUPATIONS where Occupation='Professor' order by Name) p ON p.id = m.id
left JOIN (SELECT @rownum3:=@rownum3+1 AS id, Name FROM OCCUPATIONS where Occupation='Singer' order by Name) s ON s.id = m.id
left JOIN (SELECT @rownum4:=@rownum4+1 AS id, Name FROM OCCUPATIONS where Occupation='Actor' order by Name) a ON a.id = m.id
where d.id IS NOT null or p.id IS NOT null or s.id IS NOT null or a.id IS NOT null 
```

**Highlight**
#### 1. use of `@rownum`
#### 2. There is function `pivot` in SQL Server, refer to https://www.sqlservertutorial.net/sql-server-basics/sql-server-pivot/
