# SUBQUERY

> SUBQUERY 관련 설명



## SET OPERATOR 

- 두개 이상의 쿼리 결과를 하나로 결합시키는 연산자 
- SELECT 절에  기술하는 컬럼 개수와 데이터 타입은 모든 쿼리에서 동일해야 함 

```SQL
SELECT EMP_ID, ROLE_NAME
FROM EMPLOYEE_ROLE 
UNION -- UNION ALL, INTERSECT, MINUS
SELECT EMP_ID, ROLE_NAME
FROM ROLE_HISTORY;
```

- UNION
  - 양쪽 쿼리 결과를 모두 포함(중복결과는 1번만 표현)
- UNION ALL 
  - 양쪽 쿼리 결과를 모두 포함(중복결과도 모두 표현)
- INTERSECT 
  -  양쪽 쿼리 결과에 모두 포함되는 행만 표현
- MINUS 
  - 쿼리1 포함되고 쿼리2에 포함되지 않는 행만 표현



### DUMMY COLUMN SELECT

- 목록은 반드시 동일(컬럼개수, 데이터타입) 해야하므로 DUMMY COLUMN을 사용할 수 있다.

```SQL 
SELECT EMP_NAME, HIRE_DATE
FROM EMPLOYEE
UNION 
SELECT DEPT_NAME, NULL
FROM DEPARTMENT
```



## SUBQUERY

앞뒤로 () 묶어서 표현

- 직급이 동일하고 나승원보다 급여가 많은 사람의 이름, 직원, 급여를 조회

```SQL
SELECT EMP_NAME, JOB_ID, SALARY 
FROM EMPLOYEE 
WHERE JOB_ID = (SELECT JOB_ID
                FROM EMPLOYEE
                WHERE EMP_NAME = '나승원')
AND SALARY > ( SELECT SALARY
               FROM EMPLOYEE
               WHERE EMP_NAME = '나승원');
```



### 단일행 서브쿼리

- (`=` `>=` `<=` `<` `>` )

```SQL
SELECT EMP_NAME, JOB_ID, SALARY 
FROM EMPLOYEE 
WHERE SALARY = (SELECT MIN(SALARY)
                FROM EMPLOYEE) ;
```



### 다중행 서브쿼리

#### IN, NOT IN

- NOT IN 을 다중행 서브쿼리에서 사용시 결과에 NULL이 포함되면 전체 결과가 NULL이 됨
  - 서브쿼리 결과에서는 NULL인 경우를 제외해야함

```sql
WHERE EMP_ID IN (SELECT MGR_ID FROM EMPLOYEEE)
WHERE EMP_ID NOT IN (SELECT MGR_ID FROM EMPLOYEE
                WHERE MGR_ID IS NOT NULL)
```

#### ANY 연산자

- `< ANY`  : 비교 대상 중 최대 값 보다 작음
- `> ANY`  : 비교 대상 중 최소 값 보다 큼
- `= ANY`  : IN 연산자와 동일

#### ALL 연산자

- `< ALL`  : 비교 대상 중 최소 값보다 작음
- `> ALL`  : 비교 대상 중 최대 값보다 큼



## IF ~ ELSE

IF ~ ELSE 구문을 수행하는 SQL 함수

### CASE ~ END

WHEN -- IN -- THEN -- ELSE

```SQL
CASE WHEN EMP_ID IN (SELECT MGR_ID FROM EMPLOYEE) THEN '관리자' ELSE '직원' END
```

### DECODE

```SQL
DECODE(MGR_ID, NULL, '관리자','사원')
```



## EXISTS, NOT EXISTS

- 존재 여부에 따라 TRUE 값을 반환
- 존재 여부를 확인하는 목적이므로 서브쿼리에서 특정 값을 조회할 필요가 없음

```SQL
SELECT EMP_ID,
	   EMP_NAME,
	   '관리자' AS 구분
FROM EMPLOYEE E
WHERE (EXISTS/NOT EXISTS) (SELECT NULL
                           FROM EMPLOYEE
                           WHERE E.EMP_ID = MGR_ID)
```



