# list

> list 관련 함수들



- list
  
- 순서o, 중복o, 수정o, 삭제 o
  
- list 생성

  - ```python
    a = list() 
    a = [1,2,3]
    ```
- append(), insert()

  - append는 맨뒤에 insert는 원하는 인덱스에 요소를 추가하는 함수

  - ```python
    a.append(4)
    a.insert(0,6)
    ```

- sort(),reverse() 

  - 리스트를 재배열하는 함수 

  - ```python
    a.sort()
    a.reverse()
    ```

- pop()

  - 기존 리스트에서 요소를 가져오고 삭제시킨다

  - ```python
    a.pop()
    ```

- extend() vs append()

  - ```python
    ex = [4,3]
    a.extend(ex)
    print("a - extend : ", a) # 리스트가 풀려서 들어감 [6, 5, 4, 3, 4, 3]
    a.append(ex)
    print("a - append : ", a) # 리스트 통째로 들어감 [6, 5, 4, 3, 4, 3, [4, 3]]
    ```

- 최대값, 최소값, 종합평균

  - ```
    scoreData = [1,2,3,4,5,6,7]
    print('max',max(scoreData))
    print('min',min(scoreData))
    print('sum',sum(scoreData))
    print('mean',sum(scoreData)/len(scoreData))
    ```



