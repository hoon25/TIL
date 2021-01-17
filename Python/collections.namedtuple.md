# collections.namedtuple

> 클래스없이 객체를 생성하는 방법



### 코드 개요

```python
collections.namedtuple( (변수) [변수] )
```



### 코드 생성

```python
import collections
# list 형식으로 생성
Person = collections.namedtuple("Person", ["name","id"]) 
# tuple 형식으로 생성
Person = collections.namedtuple("Person", 'name id')
# str 형식으로 생성
Emp = collections.namedtuple(("Person","name, id"))

# Emp는 변수명, class 이름은 person이다. # 헷갈릴 경우 2개를 통일 시켜도 무관

per = Person('jslim',100)
Person(name='jslim', id='100')
```



### 속성에 접근

```python
# print(per['name']) # 불가능 인덱스로 접근해야함 
print(per[1])  # 100

for idx in range(len(per)):
    print("idx {}-{}".format(idx,per[idx]))

print(per.name)  # jslim
print(per.id)    # 100

name, id = per
print(name,id) # jslim 100
```



### 코드

```python
class Emp :
    def __init__(self,name,age,dept):
        self.name = name
        self.age = age
        self.dept = dept

Emp = collections.namedtuple('Emp', ['name','age','dept']) # 위 class와 동일하게 생성된 것
emp01 = Emp("sjlim",49,"edu")
print(emp01.name, emp01.age, emp01.dept)
```

### 

