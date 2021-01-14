# comprehension

> iterable(반복가능)한 오브젝트를 생성하는 방법



### 형식

- `[]`  -  list 형식
- `{}` - set, dict 형식

```python
[출력표현식 for 요소 in sequence [if 조건식]] # list 형식
{출력표현식 for 요소 in sequence [if 조건식]} # set 형식 
{key:value for 요소 in sequence [if 조건식]} # dict 형식
```

- `()` - generator 형식

```python
(출력형식 for 요소 in collection)
```





### 코드 구현

``` python
intType = [value for value in dataset if type(value) == int] # list 형식
dataset = {value * value for value in dataset} # set 형식
dataset = {data[1]:data[0] for data in dataset.items() if data[0]>=1} # dict 형식
```

- if, else 까지 존재할 경우
  -  if,else 앞으로 옮겨짐

```python
target = [1 if t == 'spam' else 0 for t in target]
print(target)
```

- generator comprehension

```python
squareData = (num ** 2 for num in range(5)) # generator 형식
```

