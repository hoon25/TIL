# Django App

>Django App 생성 및 기본 설정



## 앱 추가

### 터미널에서 앱 추가

`python manage.py startapp (앱 이름)`

- 앱 이름의 디렉토리 생성



### urls.py 

앱 디렉토리에 urls.py 파일 만들고 url 연결

```python
from GreetingApp import views
urlpatterns = [
    path('hi/', views.hi),
]
```



### views.py

views.py에 url 함수 입력

```python
from django.shortcuts import render, HttpResponse  # httpResponse 추가

# Create your views here.
def hi(request):
    return HttpResponse('<div align = center> 섭이와 함께하는 장고 웹</div>')
```



### 접속

http://127.0.0.1:8000/greeting/hi/

