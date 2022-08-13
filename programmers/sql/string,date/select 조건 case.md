```
중성화 여부 파악하기

SELECT a.ANIMAL_ID,a.NAME, 
case when(SEX_UPON_INTAKE LIKE '%NEUTERED%' OR SEX_UPON_INTAKE LIKE '%SPAYED%')
then 'O'
else 'X'
end as '중성화'
from ANIMAL_INS as a
order by a.ANIMAL_ID ASC
```
