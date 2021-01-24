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



### 단일행 서브쿼리(= > >= <= <>)

```SQL
SELECT EMP_NAME, JOB_ID, SALARY 
FROM EMPLOYEE 
WHERE SALARY = (SELECT MIN(SALARY)
                FROM EMPLOYEE) ;
```



### 