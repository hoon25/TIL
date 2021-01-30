# control statement

> 제어문 관련 함수들(if, for, while)



## 조건문(conditional statement)

### if문

```python
if, if~else, if~elif~else
```



### 삼항 연산자

- 코드를 더 간결하게 보여줌.
- 기존

```python
result = if num > 5:
    		num * 2 
        else:
            num +2
```

- 삼항 연산자

```python
result = num * 2 if num >5 else num + 2 
```



## 반복문(repetitive statement)

### for문

```python
for ~ in range()
for ~ in list, dict
```



- list에 tuple이 있는 형식 

```python
userList = [(1,2),(3,4),(5,6)]
for tmp01, tmp02 in userList :
    userSum += (tmp01 + tmp02)
```

- list에 dict이 있는 형식

```python
userDict = {'name' : 'jslim', 'gender' : 'm'}
for (key, value) in userDict.items()  :
    print("{}, {}".format(key,value))
```



- for 구문을 통해 list 변경

```python
userList = [1,2,3,4,5,6,7,8,9]

userList02 = [tmp ** 2 for tmp in userList]  # [1, 4, 9, 16, 25, 36, 49, 64, 81]
userList03 = [tmp ** 2 for tmp in userList if tmp%2 == 0]
# if까지 사용 # [4, 16, 36, 64]
```

- for 구문을 통해 dict 변경

```python
userDict = {'TEST' + str(tmp): tmp ** 2 for tmp in range(1,10)}
print(userDict)
```



- 단어의 빈도수 구하기 

```python
for word in wordVec : 
    wordCnt[word] = wordCnt.get(word, 0) + 1  # get(해당 key의 value값을 가져옴, 0 : default)
   
for word in wordVec : 
    if word in wordCnt02 :
        wordCnt02[word] += 1    
    else :
        wordCnt02[word] = 1
```



- for else 구문

```python
search = 17
numbers = [14,3,4,7,10,24,17,2,33,15,34,36,38]

for num in numbers :
    if num == search :
        print("Found - ", num)
        break  # break, continue
else :
    print("Not Found - ", num)
```



### while문

```python
while <expression> : 
    statement 
    증감식
```



- while문 사용 위해 랜덤변수 생성후 while 문

```python
import random 
ran = random.random()  # 0~1 사이 난수를 발생(실수형)   
ran = random.randint(0,2) # 0~2 사이 난수를 발생(정수형)

randNum = random.randint(1,10)
while True :
    guessNum = int(input("예상 숫자를 입력하세요 : "))
    if randNum == guessNum :
        print("success")
        break
    elif randNum > guessNum :
        print("더 큰수를 입력")
    else :
        print("더 작은 수를 입력")
```



- 모집단 data 생성후 k개의 데이터를 샘플링

```python
# random choices()
dataset = list(range(1, 10001))

# 모집단 dataset에서 k개의 데이터를 샘플링하고 싶다면?
train = random.choices(dataset, k= 10) 
# sample dataset -  [6096, 8710, 1684, 6239, 392, 1274, 8351, 6802, 7494, 4059]
```

