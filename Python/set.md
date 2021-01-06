# set

>set 관련 함수들



- set

  - 순서X, 중복X
  - 중복제거용으로 주로 사용

- set 생성

  - ```python
    temp = {'jslim','teacher'}
    temp = set([1,2,3,4,5,5,5,5])
    ```

- union(), intersection(), difference() 

  - ```python
    print("합집합 | - ", set01|set02)
    print("합집합 union - ", set01.union(set02))
    
    print("교집합 & - ", set01&set02)
    print("교집합 intersection - ", set01.intersection(set02))
    
    print("차집합 - - ", set01 - set02)
    print("차집합 difference - ", set01.difference(set02))
    ```

- remove(), discard() 

  - remove() : 없는 것을 삭제하려 하면 오류 발생 -> debug의 발견을 위해 주로 사용

  - discard() : 없는 것을 삭제하려 해도 오류 발생 x

  - ```python
    set01.remove(9)
    set01.discard(9)
    ```

