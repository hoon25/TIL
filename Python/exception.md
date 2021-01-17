# exception

> 예외 발생시 처리하는 구문



## 예외(Exception)

### xxxxError의 종류

- SyntaxError, TypeError, NameError, IndexError, ValueError, KeyError



### 코드 개요

```python
try : 
    에러가 발생할 가능성이 있는 코드 
    정상코드 
except xxxxError:
    1. 프로그램의 흐름을 정상으로 컨트롤 
    2. 예외 발생의 디버깅
    3. 로그파일을 만들어서 예외 정보를 저장 
except xxxxError:
    발생된 에러를 잡기위한 객체 정의 
else :
    에러가 발생되지 않을 때 실행되는 블럭
finally :
    무저건 수행
```



### 코드 작성

```python
def userKeyIn():
    try :
        age = int(input("본인의 나이를 입력하세요 : "))
        print("예외 발생 이후 code")
    except Exception as e : 
        print('error =', e)
        print("문자열이 아닌 정수를 입력해주세요")
        userKeyIn()
	else : 
        print("age - ", age)
        print("함수실행 종료")
	finally : 
        print("항상 나오는 함수")
```



### 강제 오류 발생

```python
raise InsuficientError("000내용")
```

