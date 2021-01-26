# Django 시작

> Django 기본 옵션에 대한 설명



### MVT

M(Model), V(View), T(Template)



### MVT 코딩 순서 

1. 프로젝트 뼈대 만들기
   - 프로젝트 및 앱 개발에 필요한 디렉토리와 파일 생성
2. 모델 코딩하기
   - 테이블 관련 사항을 개발(models.py, admin.py)
3. URLconf 코딩하기
   - URL 및 뷰 매핑 관계를 정의(urls.py 파일)
4. 템플릿 코딩하기
   - 화면 UI 개발(templates/디렉토리 하위의 *html 파일들)
5. 뷰 코딩하기 : 어플리케이션 로직 개발(views.py 파일)



## 초기 환경 설정

### 프로젝트 생성

terminal 에 명령어 입력

- `django-admin startproject baseWeb`
- `cd (프로젝트명)`
- `dir/w`  manage.py 존재해야 함

### settings.py 

`ALLOWED_HOSTS = ['localhost','127.0.0.1']`

`TIME_ZONE = 'Asia/Seoul'`

앱 추가

- `INSTALLED_APPS = ['HelloApp']` 추가



서버실행 명령어 



