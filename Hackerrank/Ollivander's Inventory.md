### Question link: https://www.hackerrank.com/challenges/harry-potter-and-wands/problem ###
#### 2020-01-11 ####
**Answers**
```sql
select      a.id, 
            b.age, 
            a.coins_needed, 
            a.power 
from        Wands a 
inner join  Wands_Property b 
on          a.code=b.code 
where       b.is_evil!=1 
and         a.coins_needed=
            (select     min(Wands.coins_needed) 
             from       Wands 
             inner join Wands_Property 
             on         Wands.code=Wands_Property.code 
             where      Wands_Property.age=b.age 
             and        Wands.power=a.power) 
order by     a.power desc,
             b.age desc
```

**Highlight**
#### 1. Just wannt point out an really interesting opinion: 
        Hermione's reasoning is flawed. The wand chooses the wizard, not the other way around.
#### 2. Inside a subquery's `where` condition, it can linked with the query itself. 
