# Python 기초설명

> Python 첫날이므로 광범위한 기본 및 개념 위주 설명 



### Python 장점 

- 상대적으로 쉽다 
- interactive programming
- 분석, 통계에 관련된 library가 풍부하다
- Open Source(무료)
- R에 비해서 범용적 



### Python 단점 

- 하위 호환성이 없다. (하위버전을 지원하지 않음) 



### 변수

- 데이터를 담는 공간 또는 그릇 
- 숫자로 시작할 수 없다. 특수문자 허용되는데 `_ $`만 허용
- Camel Case : 함수 정의시 많이 사용하는 방법
  - ex) `numberOfCollageGraduates`
- Pascal Case : 클래스 정의시 사용하는 방법 
  - ex) `NumberOfCollageGraduates`
- Snake Case : 권장하지 않는다. 
  - ex) `number_of_collage_graduates`



### 함수 

- 행위(업무 로직 및 알고리즘)



### 클래스 

- 변수
- 함수
- 생성자 



### 데이터 타입 

- Numeric
- Sequence(list, tuple, range)
- Text Sequence (str)
- Mapping (dict) 
  - Key value로 변수를 담을 수 있는 것 
- Set (set)
  - 중복과 순서가 존재하지 않는다. 
- Bool (True(T), False(F), not, and, or (논리), &, |, ~(비교))
- Date, Timedate(날짜)



### print 함수

- print(변수, 변수, 변수)
  - ex) `print(year, month, day)`

- separator 옵션

  ```python
  print('p','y','t','h','o','n',sep = "")
  print("010","4603","2283",sep = "-")
  ```

- end 옵션(print)

  ```python
  print("Welcome To", end = ' ')
  print("IT News", end = ' ')
  ```

- format 사용법

  ```python
  one = 1
  two = 2
  print("%d %d" %(one, two))
  print("{}{}".format(one,two))
  print("{1}{0}".format(one,two))
  print("%10s" %("nice", ))
  print("%-10s" %("nice", ))
  print("%1.8f" %(3.1415934343936343)) # 소수점 8자리까지만
  print("{:1.8f}" .format(3.1415934343936343)) # 소수점 8자리까지만
  ```



###  Escape 코드 

- `\n` : 개행
- `\t` :  탭
- ` \\` : 문자 
- `\'` :  문자
- `\"` : 문자
- `\000` : 널 문자



### list 함수 

- 임의의 객체를 순서대로 저장하는 집합 자료형

- 명명법

  - ```python
    a = []
    a = list() 
    a = [1,2,3]
    b = [1,2, ['show','me','the','money'], 3.14] # 리스트안에 리스트 넣기 가능
    ```

- slicing 

  - ```python
    print(a[0:2])
    print(b[2][2:])
    print(b[2][2])
    ```



### tuple 함수 

- 명명법 

  - ```python 
    a = () 
    a = tuple() 
    a = (1,) # 하나일때는 뒤에 콤마를 추가해 줘야함 
    a = (1,2,3)
    ```

- type casting 

  - 튜플을 리스트로 타입을 바꿀 수 있음

  - ``` python
    a = list(a) 
    ```

    