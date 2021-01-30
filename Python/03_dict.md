# dict

> dict 관련 함수들



- dict

  - key와 value의 대응관계 type

- dict 생성함수 

  - ```python
    dict01 = {
        'name' : 'seop',
        'age' : 49,
        'address' : 'kwangju',
        'brith' : '730910',
        'gender' : 'm'
    }
    ```

  - ```python
    dict02 = dict([('name','seop'),('age', 49),('address' , 'kwangju'),('brith','730910'),('gender','m')])
    ```

  - ```python
    dict03 = dict(
        name = 'seop',
        age =  49,
        address = 'kwangju',
        birth ='730910',
        gender = 'm')
    ```

- dict 요소 추가

  - ```python
    dict01['marriage'] = True
    ```

- key 유무를 판단

  - ```python 
    print('marriage' in dict01)
    ```

- value 확인

  - ```python
    print('address - ', dict01['address'])
    print('address - ', dict01.get('name'))
    ```

- dict_keys, dict_values, dict_items

  - ```python
    dict03.keys() # dict_keys(['name', 'age', 'address', 'birth', 'gender']
    dict03.values() # dict_values(['seop', 49, 'kwangju', '730910', 'm'])
    dict03.items() # dict_items([('name', 'seop'), ('age', 49), ('address', 'kwangju'), ('birth', '730910'), ('gender', 'm')])
    ```

- pop(), del

  - dic 값을 삭제

  - ```python
    dict03.pop('birth')
    del dict03['gender']
    ```

- clear()

  - 전체삭제

  - ```python
    dict03.clear()
    ```



