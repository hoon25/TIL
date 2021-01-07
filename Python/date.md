# date

> date형 관련 함수들



### date 관련 라이브러리

```python
from datetime import date,datetime,timedelta
```

- date형 기본라이브러리
  - date : 날짜 
  - datetime : 시간 
  - timedelta : 날짜, 시간의 이동

```python
from dateutil.relativedelta import relativedelta
from dateutil.parser import parse
```

- 설치해야하는 라이브러리 
  - relativedelta : year,month 이동 가능
  - parse : str-date형식 변경 가능



### date 생성

```python
today = date.today() # 날짜
print('date - ', type(today), today, today.year, today.month, today.day)
```

```python
todayDateTime = datetime.today()
print('datetime - ', todayDateTime)
print("시 {}, 분 {}, 초{}". format(todayDateTime.hour, todayDateTime.minute, todayDateTime.second))
```



### 날짜 옮기기

```python
today = date.today()
days = timedelta(days = -1)
days = relativedelta(months = -2)
```



### str-date 형식 변경

```python
userDate = parse("2021-06-04") # 2021-06-04 00:00:00
userDate = datetime(2021,12,25) # 2021-12-25 00:00:00
```

### 

### 날짜형식 -> 문자열형식

```python
print("{}".format(today.strftime("%m-%d-%y"))) # 01-06-21
print("{}".format(today.strftime("%m-%d-%Y"))) # 01-06-2021
```

- 년도 y 대소문자 구별
  - Y : 0000
  - y : 00



### 문자열형식 -> 날짜형식

```python
strDate = '2021,01,06-11:12:40'
userDate = datetime.strptime(strDate, "%Y,%m,%d-%H:%M:%S") #0000이므로 Y로 지정
```

