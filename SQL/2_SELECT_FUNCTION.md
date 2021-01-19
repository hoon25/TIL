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
SUBSTR('THIS' IS A TEST')
```









