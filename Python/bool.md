# bool

> 논리형 관련 함수들



- not, and, or 

  - 논리연산

  - ```python
    print('and - ', trueValue and falseValue) # False
    print('or - ', trueValue or falseValue) # True
    print('not - ', not trueValue) # False
    ```



- & , | , ~ 

  - 비교연산

  - ```python
    print(xValue & yValue)  # 0101 & 0000 -> 0000 -> 0
    print(bool(xValue & yValue)) # False
    
    print(xValue | yValue) # 0101 | 0000 -> 0101 -> 5
    print(bool(xValue | yValue)) # True
    ```



- `and`  == `&`  차이점

  - `and`(논리연산자, True | False 연산)
    - x and y 있을 때
    - x가 False 이면 x 값을 반환
    - x가 True 이면 y값을 반환

  - `&`(비교, bitwise 연산자)

    - bitwise 연산자 : 대응되는 두 비트가 서로 다르면 1을 반환하고, 같으면 0을 반환

    

  - 간단하게 True,False일때는 `&` 사용x, 논리 연산자 사용할 것

