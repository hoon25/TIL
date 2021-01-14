# iterator,generator

>iterator(반복자)관련 함수 설명 
>
>generator는 iterator를 만들어 주는 기능



## iterable vs iterator 

- iterator 사용시 실행의 속도가 훨씬 빨라짐 

### iterable

iterable 객체 

- list, set, tuple, dict - (collection)

### iterator

- 파이썬 모듈이 가지고 있는 내장함수 `iter()`
- 순차적으로 다음 데이터를 리턴할 수 있는 객체 
- 내장함수 `next()` 사용해서, 순환하는 다음 값을 반환함



### 구현

```python
userList = [1,2,3,4,5]
userIterator = iter(userList)
print(next(userIterator))  # 실행할 때마다  # 1 2 3 4 5 순차적으로 출력
# 끝나면 StopIteration 출력
```

### 

### iterator 클래스 구현

```python
class Counter : 
    def __init__(self, stop):
        self.stop = stop 
    def __iter__(self):  # iter함수 생성
        return CounterIterator(self.stop)
    
class CounterIterator : 
    def __init__(self,stop):
        self.current = 0 
        self.stop = stop 
    def __next__(self):
        if self.current < self.stop : 
            rtnValue = self.current 
            self.current += 1
            return rtnValue
        else : 
            pass

cntIterator = iter(Counter(10))
print(next(cntIterator))
```



## generator

- iterator를 생성해주는 함수
- yield라는 키워드를 사용하여서 훨씬 간단하게 작성가능

### yield

- 잠시 함수 실행을 멈추고 호출한 곳에 값을 전달 
  - 현재 실행된 상태를 계속 유지 
  - 그러므로 다시 해당 함수를 호출하면 현재 실행된 상태를 기반으로 다음 코드를 실행

```python
def textSequenceFunc():
    msg = 'hi python'
    for txt in msg : 
        yield txt

test = textSequenceFunc()
next(test) # 실행 시 h i p y t h o n 순차적으로 출력
# 끝날 경우 StopIteration 출력
```



```python
def userGeneratorFunc(data):
    for tmp in data : 
        yield tmp*2

twiceList = userGeneratorFunc([1,2,3,4,5])
print(next(twiceList)) # 하나씩 생성 이때는 next() 사용
for t in twiceList: # 끝까지 출력되게함, 여기서는 print() 사용
    print(t)
print(sum(twiceList)) # 합을 구할 땐 print()사용
```



### generator comprehension

- `(출력형식 for 요소 in collection) `

```python
squareData = (num ** 2 for num in range(5))
```





