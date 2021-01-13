# decorator

> 함수인자로 다른 함수의 수행과정에서 적용할 수 있는 문법



## decorator 실행

- 함수 설정

```python
def outerFunc(func):
    def innerFunc() : 
        print("hi")
        func() # 함수 실행
        print("bye")
    return innerFunc

def userFunc():
    print("userFunc 함수가 수행되었습니다.")
```

- 함수 실행

```python
decoratorFunc = outerFunc(userFunc)
decoratorFunc()  # "hi" "함수가 수행되었습니다." "bye"
```



- `@`사용해서 간편하게 실행

```python
@outerFunc
def userFunc():
    print("함수 실행")
    
userFunc() # "hi" "함수 실행" "bye"
```



- 파라미터와 관계없이 모든 함수에 적용 가능한 Decorator 만들기
  - `* args`  `**kwargs`

```python 
def generalDeco(func):
    def wrapper(*args, **kwargs):
        print("this is decorated")
        return func(*args, **kwargs)
    return wrapper
```



- Decorator 두개 사용
  - 가장 가까운 데코레이터부터 실행됨
  - makeFont 실행 후 makeBold 실행

```python
@makeBold
@makeFont
def makeBoldFont(string):
    return string
```



