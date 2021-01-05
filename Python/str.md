# 파이썬 str

> str형 관련 함수 정리



## dir()

- ```python
  print(dir(seqText)) # 함수, 모듈, 데이터 타입
  ```



## str

- indexing

  - ```python
    seqText[3]
    ```

- slicing

  - ``` python 
    print(seqText[0:4])
    print(seqText[-6:])
    print(seqText[ : : 2]) # 2step 건너 출력
    print(seqText[ : : -2]) # 꺼꾸로 2step 건너 출력
    ```

- replace()

  - 문자를 치환하는 함수

  - ```python
    phoneNumber.replace('-'," ")
    ```

- split()

  - 문자열을 쪼개는 함수

  - ```python
    urlSplit = url.split('.')
    ```

- strip(), rstrip(), lstrip()

  - 문자열에서 공백 제거 함수

  - ```python
    companyName.strip()
    companyName.rstrip()
    companyName.lstrip()
    ```

- upper(), lower()

  - 대문자, 소문자 변환 함수 

  - ```python
    companyName.upper()
    companyName.lower()
    ```

- capitalize()

  - 문자열의 맨 앞글자만 대문자가 됨

  - ```python
    string.capitalize()
    ```

- endswith()

  - 끝에 오는 문자열에 해당 여부 논리값으로 반환

  - ```python
    fileName = 'report.xls'
    isExits = fileName.endswith(('xls', 'xlsx', 'csv')) # True
    ```

- in, not in 

  - 문자열에 존재 여부 논리값으로 반환

  - ```python
    myStr = "This is a sample Text"
    print("sample" in myStr)
    print("text" not in myStr)
    ```

- count()

  - 문자의 빈도

  - ```python
    brandName.count('c')
    ```

- find(), index()

  - 문자열에서 문자의 위치 찾기

  - find()는 해당값 없을경우 -1 반환

  - index()는 해당값 없을경우 오류 발생

  - ```python
    brandName.find('a')
    brandName.index('a')
    ```