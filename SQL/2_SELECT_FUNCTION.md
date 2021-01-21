# SELECT

> SELECT구문 함수 및 추가 Option



## 문자열 함수

### LENGTH

문자의 갯수를 반환하는 함수 

- 문자열 `CHAR`(고정길이), ` VARCHAR2`(가변길이)

CHARTYPE에 한글이 있을 경우 계산 공식이 다름

- 한글 1문자 - 3BYTE, 
- EX) 3*6글자 = 18BYTE  //  CHAR 20BYTE  20-18 =2 // 6+2 = `8`
  - 이렇기 때문에 VARCHARTYPE을 추천함

```SQL
SELECT LENGTH(CHARTYPE)
```

### LPAD/RPAD

문자열에 길이를 덧붙이는 함수 

- 정렬효과를 가져오기 위해서 사용하는 경우도 많다

```SQL
L/RPAD(string, N, [str])
LPAD(EMAIL,30,' ')
RPAD(EMAIL,30,'.')
```

### TRIM/LTRIM/RTRIM

문자를 제거할 때 사용하는 함수

- 지정한 STR에 포함된 모든 문자를 제거
- 패턴을 제거하는 의미가 아님 

```SQL
TRIM('   TEST   ') --TEST
LTRIM('123123TEST','123') --TEST
LTRIM('XYZYYYTEST','XYZ') -- TEST
RTRIM(LEADING '1' FROM 'TEST1')
```

- `TRIM`구문에서 `LEADING`,`TRAILING`을 이용해서 LTRIM,RTRIM 구현가능

```SQL
TRIM(LEADING '1' FROM 'TEST1') -- LEFTTRIM  / --TEST1
TRIM(TRAILING '1' FROM '123TEST111') --RIGHTTRIM / -- 123TEST
```

### SUBSTR

주어진 컬럼/ 문자열에서 지정한 위치부터 지정한 개수만큼의 문자열을 잘라내어 반환하는 함수 

```SQL
SUBSTR(string, position, [length])
SUBSTR('THIS IS A TEST', 6, 2) -- IS
SUBSTR('THIS IS A TEST', 6) -- IS A TEST
SUBSTR('TechOnTheNet', -3,3) -- Net
SUBSTR('TechOnTheNet', -8) -- OnTheNet
```

### 

## 숫자함수

### ROUND

지정된 자릿수에서 반올림 하는 함수 

```SQL
ROUND(number, [demical_places])
ROUND(125.315) -- 125  --default : 0
ROUND(125.315,1) -- 125.3
ROUND(125.315,-1) -- 130
```

### CEIL/TRUNC

지정된 자릿수에서 올림/내림 하는 함수 

- `CEIL` - 올림

- `TRUNC` - 내림



## 날짜함수

### SYSDATE

현재날짜와 시간을 표시하는 함수 

- 기본설정형식 : YY/MM/DD

```SQL
SELECT SYSDATE - 20/01/18
```

### ADD_MONTHS

지정한 만큼의 달 수를 더한 날짜를 반환하는 함수 

```sql
ADD_MONTHS(date, N)
ADD_MONTHS(HIRE_DATE, 240)
```

### MONTHS_BETWEEN

지정한 두 날짜 사이의 월 수를 반환하는 함수 

- date1 > date 2 : 양수 반환
- date1 < date 2 : 음수 반환 

```SQL
MONTHS_BETWEEN(date1, date2) 
```



## 데이터타입변환 함수

### TO_CHAR

NUMBER/DATE 타입을 CHARACTER 타입으로 변환하는 함수

DATE 타입 변환

- YYYY/YY/YEAR (4자리숫자/뒤 2자리숫자ㅏ)
- MONTH/MON/MM/RM (이름/약어/숫자/로마 기호)

- DDD/DD/D 일(1년 기준/ 1달 기준/ 1주 기준)

- Q 분기(1,2,3,4)
- DAY/DY 요일(이름/ 약어 이름)
- HH(12), HH24 (12시간, 24시간)
- AM|PM 오전, 오후
- MI  분 (0~59)
- SS 초 (0~59)



NUMBER 타입 변환

- `9` 자리수 지정
- `0` 남는자리를 0으로 표시
- `$` 또는 `L` 통화기호 표시
- `.`또는 `,`  지정한 위치에 . 또는 , 표시
- `EEEE` 과학 지수 표기법

```SQL
SELECT T0_CHAR(1234,'99999') --1234
SELECT T0_CHAR(1234,'09999') --01234
SELECT T0_CHAR(1234,'L99999') --\1234 
SELECT T0_CHAR(1234,'99,999') --1,234 
SELECT T0_CHAR(1234,'09,999') --01,234 
SELECT T0_CHAR(1234,'9.9EEEE') --1.0E+03
SELECT T0_CHAR(1234,'999') -- ####
```



### TO_DATE

CHARACTER 타입을 DATE 타입으로 변환하는 함수

```SQL
TO_DATE(input_type,[format])
TO_DATE('20100101','YYYYMMDD')
```



RR날짜 형식

- 0-49 50-99 기준

```SQL
TO_CHAR(TO_DATE('95/10/27','RR/MM/DD'), 'RRRR/MM/DD') --1995/10/27
```



### NVL

NULL을 지정한 값으로 변환하는 함수

```SQL
NVL(expr1, expr2)
SELECT EMP_NAME, SALARY, NVL(BONUS_PCT,0)
```



## 단일 행 조건함수

### DECODE

SELECT 구문으로 IF-ELSE 논리를 제한적으로 구현한 오라클 DBMS 전용 함수

```SQL
DECODE(expr, search1, result1 [,searchN, resultN] [,default])
DECODE(SUBSTR(EMP_NO,8,1),'1','남','3','남','여')
DECODE(MGR_ID, NULL, '없음', MGR_ID) -- NULL값 처리 시 NVL 함수와 동일한 결과
```



### CASE

DECODE 함수와 유사

- ANSI 표준구문으로 더 많이 사용됨

```SQL
CASE expr WHEN search1 THEN result1 [WHEN.. THEN..][ELSE default] END
CASE WHEN condition1 THEN result1 [WHEN.. THEN..][ELSE default] END

SELECT CASE JOB_ID
		WHEN 'J7' THEN TO_CHAR(SALARY * 1.1)
		WHEN 'J6' THEN TO_CHAR(SALARY * 1.15)
		ELSE TO_CHAR(SALARY*1.05) 
		END AS 인상급여
		
SELECT CASE WHEN SALARY <=300000 THEN '초급'
			WHEN SALARY <=400000 THEN '중급'
			ELSE '고급' END AS 구분
```



## 그룹 함수

### SUM

- 총합 계산

### AVG

- 평균 계산
- NULL을 제외하므로 결과가 달라질 수 있음

### MIN

- 최소 값 반환
- DATE 타입 : 가장 오래 전 날짜를 의미
- CHARACTER 타입 : 해당 character set의 내부 값이 가장 작은 문자를 의미 

### MAX 

- 최대 값 반환
- DATE 타입 : 가장 최근 날짜를 의미 
- CHARACTER 타입 : 해당 character set의 내부 값이 가장 큰 문자를 의미

### COUNT 

- Result Set 전체 행 수 반환


```sql
SUM/AVG/MAX/MIN(SALARY)
COUNT(*) -- Result Set의 전체 행 수 반환
COUNT(DISTINCT expr) -- NULL과 중복 값을 제외한 행 수 반환
COUNT(expr) -- expr에 포함된 값 중 NULL을 제외한 행 수 반환
```

