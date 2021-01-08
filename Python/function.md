# function

> python의 함수기능 정리 



### function

```python
def functionName() : 
    statement
    return value(built - in Type)
```



### package, module

- 함수는 내장함수와 사용자정의 함수가 있다. 
- 사용자 정의 함수는 사용자가 python package를 만들고  그 안에 module에서 함수를 관리한다. 



### 사용자 정의 함수 호출

```python 
# 'digital' 패키지 안에 'python' 패키지가 있고 그 안에 packageFunction.py 모듈이 있음.

from digital.python import packageFunction  # 이것을 기본으로 이해
packageFunction.printCoins()

from digital.python import packageFunction as f
f.printCoins()

from digital.python.packageFunction import * 
# * 모든것을 다 가져오는것으로 좋은방식은 아님(메모리 낭비)
printCoins()
```

- packageFunction.py

```python
def printCoins():
    print("bitcoin")
```



### tuple, dic 타입을 가변인자로 받기

```python
# tuple 타입을 가변인자로 받겠다
def tupleFunc(*args) : # 가변인자의 수를 지정하지 않아도 된다.
    result = 0
    for idx in range(len(args)) :
        result += args[idx]
    return result

tupRtn = f.tupleFunc(1,2,3,4,5,6,7,8,9)
print('call tupleFunc() - ', tupRtn)


#  dic 타입을 가변인자로 받겠다
def dictFunc(**args) :
    for key,value in args.items() :
        print("{} = {}".format(key,value))

f.dictFunc(name = 'jslim')

# 추가) dict형식을 넣을 땐 위와 같은 방식으로
personInfo(54, 177, name = '섭섭해', address = 'seoul')  
```



### default parameter

- 인자를 할당하지않을 경우 자동으로 default 값으로 설정

```python
def defaultParam(x, y, z = True):  # 인자값이 할당되지 않을 경우 True로 자동 할당
    paramSum = x + y
    if paramSum > 10 and z :
        return paramSum
    else :
        return 0

result = defaultParam(10,20)    # 10, 20, True로 적용됨, python에서만 가능
```



### 입력인자의 가변/불변

- 함수의 입력인자가 list, dict  : mutable(가변)
- 함수의 입력인자가 숫자, 문자열, tuple  :  immutable(불변)



### local / global

- 함수 내부에서 지정하면 local 변수 
  - `global (변수)`  -  함수 내부에서 global 변수로 지정



### nested function(중첩함수)

- 함수 안에 함수가 있는 구조
  - outer 함수 : 자료(data) 생성, inner 함수 포함 
  - inner 함수 : 자료 연산/처리(합계,평균)

```python
def outerFunc(num) :
    def innerFunc(num):
        print('innerFunc - ' ,num)
    innerFunc(num + 100)

outerFunc(200) # 300
```

```python
def calcFunc(data):
    dataset = data

    def sumFunc() :
        total = sum(dataset)
        return total
    def avgFunc(total) :
        avg = total / len(dataset)
        return avg
    return sumFunc, avgFunc  # 함수의 반환도 가능함

data = list(range(1,101))
print('range data - ', data) # [1, 2, 3......100]

rtnSumFunc, rtnAvgFunc = calcFunc(data)
tot = rtnSumFunc()
print(tot) # 5050
avg = rtnAvgFunc(tot)
print(avg) # 50.5
```



### 재귀함수

- 함수 내부에서 자신의 함수를 반복 호출하는 기법
- 용도 : 반복적으로 변수를 변경해서 연산할 때(누적, 팩토리얼)

```python
def countFunc(n) : # n = 5 -> 1,2,3,4,5
    if n == 0 :
        return 0
    else :
        countFunc(n-1)   # stack[5,4,3,2,1]에 쌓임  역순으로 빠져나가게 됨.
        print(n, end = ' ')

countFunc(5) # 1 2 3 4 5
countFunc(0) # 0
```



### lambda함수 

- 가독성 향상, 코드 간결, 메모리 절약
- 하지만 무분별하게 사용할 경우 코드 가독성 떨어짐



```python
def multiFunc(x,y) :
    return x * y
print(multiFunc(10,50))

# 위에 함수를 lambda식으로 바꿨음
# syntax : lambda arg : body
lambdaVar = lambda x, y : x * y
print(lambdaVar(10,50))

def lambdaFunc(x,y, func) : # 함수의 인자로 함수를 넘겨줄 수 있음
    print('lambdaFunc - ', x * y * func(100,100))

lambdaFunc(10,20, lambda x, y : x * y)  # 10 * 20 * 100 * 100  = 2000000
lambdaFunc(10,20, lambdaVar)
lambdaFunc(10,20, multiFunc)
```



### 함수 입력인자 데이터 설정

```python
def totalLengthFunc(word : str, num : int):
    pass 
```

