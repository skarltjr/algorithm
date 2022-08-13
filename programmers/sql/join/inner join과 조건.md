```
있었는데요 없었습니다

SELECT a.ANIMAL_ID,a.NAME from ANIMAL_OUTS as a join ANIMAL_INS as b on a.ANIMAL_ID = b.ANIMAL_ID
where a.DATETIME < b.DATETIME
order by b.DATETIME
```
