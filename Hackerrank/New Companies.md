### Question link: https://www.hackerrank.com/challenges/the-company/problem ###
#### 2020-01-13 ####
**Answers 1**
```sql
SELECT  c.company_code,
        c.founder,
        count(distinct(lm.lead_manager_code)),
        count(distinct(sm.senior_manager_code)),
        count(distinct(m.manager_code)),
        count(distinct(e.employee_code))
FROM Company c
LEFT JOIN   Lead_Manager lm  
ON          c.company_code=lm.company_code
LEFT JOIN   Senior_Manager sm  
ON          c.company_code=sm.company_code
AND          lm.lead_manager_code=sm.lead_manager_code
LEFT JOIN   Manager m  
ON          c.company_code=m.company_code
AND          lm.lead_manager_code=m.lead_manager_code
AND          sm.senior_manager_code=m.senior_manager_code
LEFT JOIN   Employee e  
ON          c.company_code=e.company_code
AND          lm.lead_manager_code=e.lead_manager_code
AND          sm.senior_manager_code=e.senior_manager_code
AND          m.manager_code=e.manager_code
GROUP BY    1,2
ORDER BY    1
```
#### The code seems so redundant when using 4 consecutive joins, instead there is another way to do it simpler

**Answers 2**
```sql
select c.company_code, c.founder, 
    count(distinct l.lead_manager_code), count(distinct s.senior_manager_code), 
    count(distinct m.manager_code),count(distinct e.employee_code) 
from Company c, Lead_Manager l, Senior_Manager s, Manager m, Employee e 
where c.company_code = l.company_code 
    and l.lead_manager_code=s.lead_manager_code 
    and s.senior_manager_code=m.senior_manager_code 
    and m.manager_code=e.manager_code 
group by 1,2 order by c.company_code;
```
#### Use "Advanced Select" technique rather than "Advanced Join" technique.

**Answers 3**
```sql
select C.company_code, 
       C.founder, 
       COUNT(DISTINCT E.lead_manager_code), 
       COUNT(DISTINCT E.senior_manager_code), 
       COUNT(DISTINCT E.manager_code), 
       COUNT(DISTINCT E.employee_code) 
              from Company C
              INNER JOIN Employee E ON C.company_code = E.company_code
              GROUP BY C.company_code, C.founder
              ORDER BY C.company_code ASC;
```
