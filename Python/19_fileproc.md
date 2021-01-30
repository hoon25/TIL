# fileProc

> 파일 생성,수정 하는 함수 



### open

`open(file = '파일경로/파일명', mode = 'r|w|a|wb')`

- wb는 비트단위로 주고받는 것 프로그램 단위에서는 쓸일이 없다. 

`file.write("Hi Seop")`

`file.close() `



### with

- `file.close()` 를 하지 않아도 된다.

```python 
with open(file = 'hello.txt',mode = 'r') as file
	print(file.read())
```



- 대부분 파일은 `utf-8`로 이뤄져있음		
  - `encoding = 'utf-8'`을 포함시켜줘야한다.

```python
with open(fileName, mode,encoding = "utf-8") as file:
```



