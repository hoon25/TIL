# oop

>Objected Oriented Programming(OOP) ( 객체지향프로그래밍) 



### 설명

- 패키지(package) > 모듈(module) > 클래스(class) > 함수(function)



Real world         추상화		P/G

object ----------    class    ----> instance

- 같은 객체지만 Object는 Realworld에 존재하는 객체, instance는 P/G에 존재하는 객체 

- 변수나 함수는 class의 소속이 아닌 instance의 것



### class vs instance

- namespace : 객체를 인스턴스화 할 때 저장된 공간 
- class variable : 직접 접근가능 및 공유 
- instance variable : 객체소유로 별도 존재 



## class

- 함수의 모임 
- 역할 : 여러개의 함수와 공유데이터를 묶어서 객체를 생성할 수 있는 템플릿 
- 구성 : 멤버 = 변수(데이터) + 매서드(함수) , 생성자(초기화) 



### 기본 class 생성

```python
class Calc :  # class 생성명 첫글자 대문자
	x = 0 
	y = 0 

    def __init__(self): 
        print("객체 생성 시 호출되는 함수이고 난 초기화라고 불러줘")

    def plus(self):
        print("사용자 정의 함수, 인스턴스의 소유")
```

### instance 생성 

```python
obj = Calc() # 객체 생성 시 호출되는 함수이고 난 초기화라고 불러줘
obj.plus() # 사용자 정의 함수, 인스턴스의 소유
```



### class 생성(내장함수, 사용자 정의 함수)

```python
class Student: 
    def __init__(self, name, major, num, grade):
        self.name = name  # 앞에 self가 붙으면 instance 소유, 아래 동일
        self.major = major
        self.num = num
        self.grade = grade
        
	def __repr__(self): # 내장함수
        return self.name + self.major + self.num + self.grade
    
    def getInfo(self): # 사용자 정의 함수
        return "이름 : {} \t 전공 : {}".format(self.name, self.major)
```

### 내장함수 불러오기

```python
stu01 = Student('임섭순','컴공','1992',4.5)
print(stu01) # 임섭순 컴공 1992 4.5  # 내장함수 명명(= stu01.__repr__)
```

### 하나씩 불러오기 

```python 
print(stu01.name)
print(stu01.major)
```



### class 생성(클래스 소유 변수)

```python
class Student:

    scholarshipRate = 3.5  # class variable(클래스 소유) 
    					   # global, local의 개념으로 절대보면 안됨!!! 이것은 oop

    def __init__(self, name, major, num, grade):
        self.name = name   
        self.major = major
        self.num = num
        self.grade = grade

    def isScholarShip(self):
        if self.grade >= Student.scholarshipRate : 
            # 클래스 소유의 변수는 클래스의 이름으로 변수에 접근해야 함.
            # self.scholarshipRate해도 문제 없는데요?
            # class소유인건 맞지만 python은 namespace라는 것을 가지고 있다.
            # namespace(instance -> class -> superclass) 
            # 일단 instance가 class를 가지고 있기 때문에, 자동으로 찾을 수 있음

            return True
        else :
            return False
```



### class 생성(클래스 method)

```python
class Employee :

    raiseRate = 1.1 # 급여 인상률

    def __init__(self,name, salary):
        self.name = name
        self.salary = salary
    def getSalary(self):
        return '현재 {}님의 급여는 {}입니다'.format(self.name, self.salary)

    @classmethod # 클래스 소속의 method는 decorator(@)를 앞에 붙여줘야 한다!
    def updateRate(cls, rate):
        cls.raiseRate = rate
        print("인상률이 {}로 변경되었습니다.".format(rate))

    def applyRaise(self):
        self.salary = int(self.salary * Employee.raiseRate)

    # static 함수
    @staticmethod
    # (cls, self 아무것도 들어가지 않음)
    def isValid(salary):
        if salary < 0 :
            print("음수가 될 수 없습니다.")
```

### 객체 생성

```python
emp01 = Employee("임정섭",1000) 
print("연봉 인상 전 급여 - ", emp01.getSalary())  
# 연봉 인상 전 급여 -  현재 임정섭님의 급여는 1000입니다


Employee.updateRate(1.5)  # 인상률이 1.5로 변경되었습니다.
emp01.applyRaise() 	 	  # 인상률 적용

print("인상 후 급여 - ", emp01.getSalary())  # 인상 후 급여 -  현재 임정섭님의 급여는 1500입니다
```



### 추가정리

- 사용자 정의함수 명명
  - setxxxx : 묶는 함수들
  - getxxxx : 반환하는 함수들
  - isxxxx : True와 False를 주로 리턴하는 함수들