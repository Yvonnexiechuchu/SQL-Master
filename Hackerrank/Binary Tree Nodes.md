
### Question link: https://www.hackerrank.com/challenges/binary-search-tree-1/problem ###
#### 2020-01-09 ####
**Answers**
```sql
select N,
case when P is NULL then 'Root'
     when N in (select distinct P from BST) then 'Inner'
     else 'Leaf'
end as NType
from BST
order by N
```

**Highlight**
#### 1.order of operation when using `case when` 
#### 2. Subquery
