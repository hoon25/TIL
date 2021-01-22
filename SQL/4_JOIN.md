# JOIN

> JOIN 함수에 대해서 설명



### JOIN

- 서로 연관되고 다른 테이블에 존재하는 컬럼들을 한번에 조회하기 위해 사용하는 대표적인 기법 



### ORACLE 전용 JOIN 구문

```SQL
SELECT EMP_NAME, DEPT_NAME
FROM EMPLOYEE E,
	 DEPARTMENT D 
WHERE E.DEPT_ID = D.DEPT_ID;
```



### ANSI 표준 구문

`USING` : 조인조건으로 사용하는 컬럼 이름이 동일한 경우 사용

`ON` : 컬럼 이름이 서로 다른 경우 사용

```SQL
JOIN DEPARTMENT USING(DEPT_ID)
JOIN LOCATION ON (LOC_ID = LOCATION_ID)
```

