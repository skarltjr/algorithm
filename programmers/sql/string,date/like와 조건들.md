```
이름에 el 들어가는 동물 찾기

SELECT a.ANIMAL_ID,a.NAME from ANIMAL_INS as a
where (a.NAME like '%EL%' or a.NAME like '%el%') 
and a.ANIMAL_TYPE='Dog'
order by a.NAME ASC
```
