
### Question link: https://www.hackerrank.com/challenges/the-pads/problem ###
#### 2020-01-04 ####
**Answers**
```sql
select concat(Name,'(',substring(Occupation,1,1),')')
from OCCUPATIONS
order by Name;

select concat('There are a total of ',ct, ' ', lower(Occupation),'s.')
from(
SELECT Occupation,
count(Occupation) as ct
from OCCUPATIONS
group by Occupation) as temp
order by ct,Occupation
```

**Highlight**
#### 1. use of `CONCAT`, `SUBSTRING (STRING, START, LENGTH)`
#### 2. Subquery
