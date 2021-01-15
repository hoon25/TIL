# composition

>모든걸 가져가지 않고, 부모의 구성요소 중 몇개만 가져가는 기능



## composition == aggregation

- 상속을 피하고 클래스의 일부 기능을 그대로 활용하고 싶을 때 

```python
class Calc02(object):
    def __init__(self, x,y):
        self.x = x
        self.y = y
    def multiply(self):
        return self.x * self.y

class UserCalc :
    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.cal02 = Calc02(x,y)  # 객체를 명시적으로 생성  # super() 방식은 묵시적

    def multiply(self):
        return self.cal02.multiply() # 함수는 이렇게 호출 하면 됨
```

