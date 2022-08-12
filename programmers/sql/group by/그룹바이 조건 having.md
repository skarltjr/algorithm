```
동명 동물 수 찾기
SELECT a.NAME,COUNT(a.NAME) from ANIMAL_INS as a GROUP BY a.NAME HAVING COUNT(a.NAME)>1 and a.NAME is not null ORDER by a.NAME
```
