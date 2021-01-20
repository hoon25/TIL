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





### 









