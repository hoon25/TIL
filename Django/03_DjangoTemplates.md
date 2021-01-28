# Django templates

> templates



### templates

templates 디렉토리 생성

- 반드시 이름을 지켜줘야한다



#### .html 파일 생성

- `{{변수명}}`  
  - print
- `{{% %}}`
  -  code (if,for,path)



### 호출

```python
path('login/',views.login, name = 'msg') 
# name = 000 지정하면 {% url '000' %}로 호출가능
```

```html
<form method = "post" action = "../login/">  // 상대경로
<form method = "get" action = "http://localhost:8000/hello/login/"> //절대경로
<form method = "get" action = "{% url 'msg'}"> // Django 에서 지향하는 방식
```



### get/post 방식

- post 방식은 `{% csrf_token %}`을 추가해줘야 한다

```html
<form method = "post" action = "../login/">
    {% csrf_token %}
```




### 단락정리

`<p/>` 단락

`<br/>` 줄

`&nbsp` 띄어쓰기