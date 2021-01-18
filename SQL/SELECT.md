# SELECT

> select 구문에 대한 이해 



### Rule

- 명령어는 대문자를 사용
- 데이터명은 대/소문자 구별

```sql
SELECT * 
FROM EMPLOYEE;
```



### AS

컬럼명을 바꾸는 명령어

- 반드시 문자시작
- 특수부호가 들어가거나, 뛰어쓰기가 있다면 " " 해줘야함
- 컬럼 값에 대한 연산을 식으로 작성할 수 도 있음

```SQL
SELECT EMP_NAME AS '이        름',
       EMP_NO AS 주민번호
       (SALARY + (SALARY * BONUS_PCT)) * 12  AS 연봉
FROM EMPLOYEE;
```

더미컬럼

- 새로운 컬럼도 생성가능

```sql
SELECT '재직' AS 근무여부
FROM EMPLOYEE;   
```



### DISTINCT

- 값의 중복을 제거할 때 사용하는 키워드 

```SQL
SELECT DISTINCT JOB_ID
FROM EMPLOYEE;
```



### WHERE

- AND, OR

```SQL
SELECT EMP_NAME,
       DEPT_ID,
       SALARY
FROM EMPLOYEE
WHERE DEPT_ID = 90 AND SALARY > 2000000;
```



### 비교연산자

` =` ,` >` , `>= `, `<` , `<=` , `!=`

` BETWEEN AND`, `LIKE`,` IS NULL`, `IN`



#### BETWEEN AND

- 상한값과 경계값을 포함하는 경우
- (>=, <= 가능), (>,< 불가능) 

```sql
WHERE SALARY BETWEEN 3500000 AND 5500000;
```



#### 비교연산자

- `%`(Percentage) : % 부분에는 임의 문자열(0개 이상의 임의의 문자)이 있다는 의미
- `_`(Underscore) : _ 부분에는 문자 1개가 있따는 의미

```sql
WHERE EMP_NAME LIKE '김%';
```

#### ESCAPE 작성법

- ESCAPE는 원하는데로 지정가능

```sql
WHERE EMAIL LIKE '___#_%' ESCAPE '#';
```



#### IN

- OR 과 같은 의미

```SQL
WHERE DEPT_ID IN ('90','20') ;
```



#### NULL

- 컬럼값의 NULL은 `= NULL`로 찾을 수 없음
- `IS NULL`, `IS NOT NULL` 명령어 사용

```SQL
WHERE DEPT_ID IS NULL AND BONUS_PCT IS NOT NULL;
```



### 문자열 작성법

- `||` - 연결연산자
- `[컬럼 || 컬럼] [컬럼 || '문자열']`

```SQL
SELECT EMP_ID||'의월급은'||SALARY||'원입니다'
FROM EMPLOYEE;

SELECT EMP_NAME, PHONE
FROM EMPLOYEE 
WHERE PHONE LIKE '___9_______';
```



