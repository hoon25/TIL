# tuple

> tuple 관련 함수들 



- tuple
  - 순서o, 중복o, 수정x, 삭제x 
  - 읽기 전용(immutable)(불변)

- tuple 생성

  - ```python
    myTuple = ("반도","강철비2","아이언맨")
    oneTuple = (1,) # tuple안에 값이 하나일 경우 뒤에 쉼표를 하나 더 붙여줘야함
    myTuple = 1,2,3,4,5 # 이런방식으로도 생성가능
    ```

- indexing

  - list와 방식 동일

- casting 

  - 수정이 필요할 경우 리스트로 변경하여 수정가능

  - ```python
    multiList = list(multiTuple[2:])
    ```

- 1~99까지의 정수 중 짝수만 저장된 튜플을 생성

  - ```python 
    even = tuple(range(2,100,2))
    ```