# SELECT

> GROUP_FUNCTION(ORDER BY, GROUP BY, HAVING)



### ORDER BY 

SELECT 구문 실행 결과를 특정 컬럼 값 기준으로 정렬할 때 사용

```SQL
SELECT FROM WHERE 
ORDER BY 기준1[ASC|DESC]

ORDER BY DEPT_ID DESC, HIRE_DATE, EMP_NAME;
ORDER BY 부서코드 DESC, 입사일, 이름;
ORDER BY 3 DESC, 2, 1 ; 
```



### GROUP BY

GROUP BY 절에 기술한 컬럼이나 표현식을 기준으로 데이터 그룹 생성

- SELECT 절에 기술한 컬럼 중, 그룹 함수에 사용되지 않은 컬럼은 GROUP BY 절에 반드시 기술되어야 함

제약사항

- WHERE 절에는 그룹함수를 사용할 수 없음 
- GROUP BY 절에는 컬럼 이름만 사용 가능(별칭, 순서 사용 불가)

```SQL
SELECT DEPT_ID AS 부서,
		ROUND(AVG(SALARY), -4) AS 평균급여 
FROM EMPLOYEE
GROUP BY DEPT_ID
```



### HAVING

GROUP BY에 의해 그룹화 된 데이터에 대한 그룹함수 실행결과를 제한하기 위해 사용

- WHERE 는 테이블에 포함된 원본 데이터를 제한하기 위해 사용

``` SQL
SELECT DEPT_ID, SUM(SALARY)
FROM EMPLOYEE
GROUP BY DEPT_ID 
HAVING SUM(SALARY) > 9000000
```

