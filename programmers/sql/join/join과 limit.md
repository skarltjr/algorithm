```
오랜 기간 보호한 동물

SELECT a.NAME,a.DATETIME from ANIMAL_INS as a left join ANIMAL_OUTS as b
on a.ANIMAL_ID = b.ANIMAL_ID
where b.ANIMAL_ID is null
order by a.DATETIME ASC
LIMIT 3
```
