# Framework
> Framework 이해하기
- 서비스 개발에 필요한 기능들을 미리 구현해서 모아놓은 것
- Frame(뼈대, 틀) + Work(일하다)
  -  일정한 뼈대, 틀을 가지고 일하다
  -  제공받은 도구들과 뼈대, 규약을 가지고 무언가를 만드는 일
  -  특정 프로그램을 개발하기 위한 여러 도구들과 규악을 제공하는 것
- 소프트웨어 프레임워크는 복잡한 문제를 해결하거나 서술하는 데 사용되는 기본 개념 구조


# 클라이언트와 서버
- 클라이언트 - 서버 구조
  - 오늘날 우리가 사용하는 대부분의 웹 서비스는 클라이언트-서버 구조를 기반으로 동작
  - 클라이언트와 서버 역시 하나의 컴퓨터이며 이들이 어떻게 상호작용하는지에 대한 간소화된 다이어그램은 다음과 같음

### 클라이언트
- 웹 사용자의 인터넷에 연결된 장치(ex. wi-fi에 연결된 컴퓨터 또는 모바일)
- Chrome 또는 Firefox와 같은 웹 브라우저
- 서비스를 요청하는 주체
  
### 서버
- 웹 페이지, 사이트 또는 앱을 저장하는 컴퓨터
- 클라이언트가 웹 페이지에 접근하려고 할 때 서버에서 클라이언트 컴퓨터로 웹 페이지 데이터를 응답해 사용자의 웹 브라우저에 표시됨
- 요청에 대해 서비스를 응답하는 주체


### 상호작용 예시
- 예를 들어, 우리가 Google 홈페이지에 접속한다는 것은 무엇을 뜻하는지 알아보자
  1. 결론적으로 인터넷에 연결된 전세계 어딘가에 있는 구글 컴퓨터에게 'Google 홈페이지.html' 파일을 달라고 요청하는 것
  2. 그러면 구글 컴퓨터는 우리의 요청을 받고 'Google 홈페이지.html'파일을 인터넷을 통해서 우리 컴퓨터에게 응답해줌
  3. 그렇게 전달받은 Google 홈페이지.html 파일을 웹 브라우저가 우리가 볼 수 있도록 해석해주는 것

- 여기서 'Google 홈페이지.html'을 달라고 요청한 컴퓨터, 웹 브라우저를 클라이언트라고 하고 'Google 홈페이지.html' 파일을 제공한 컴퓨터, 프로그램을 서버라고 함
- 어떠한 자원을 달라고 요청하는 쪽을 클라이언트라고 하고 자원을 제공해주는 쪽을 서버라고 함

### 정리
- 우리가 사용하는 웹은 클라이언트-서버 구조로 이루어져 있음
- 앞으로 우리가 배우는 것도 이 클라이언트-서버 구조를 만드는 방법을 배우는 것
- 이 중에서 Django는 서버를 구현하는 웹 프레임워크
# 가상환경 사용하기
- 가상환경 생성
  - python -m venv venv
- 가상환경 활성화
  - sourse venv/Scripts/activate
- 가상환경 비활성화
  - deactivate
- 가상환경 패키지 목록 저장
  - pip freeze > requirements.txt
- 파일로부터 패키지 설치
  - pip install -r requirements.txt

> 가상환경에 장고 만들기
1. 프로젝트를 위한 폴더를 생성한다.
    1. `mkdir 프로젝트 폴더명`
    
2. 프로젝트 폴더를 우클릭하여 vscode 로 열어준다.
    
    
3. `.gitignore` 파일을 생성한다.
    1. `touch .gitignore` : 터미널 명령어 → git bash 창에서 작업을 한다면
    2. [gitignore.io](http://gitignore.io) 에서 `visualStudioCode`, `python`, `django` 를 선택해서 복붙한다.
    
4. 가상환경을 설정한다.
    1. `python -m venv venv` ⇒ “python -m venv 가상환경폴더명” 형태 (폴더명 : venv 권장)
    
5. 가상환경 활성화
    1. `source venv/Scripts/activate` : source v 탭 s 탭 a 탭
    2. Mac 에서는 (venv/Bin/activate)
    3. 활성화가 되었다면 상단에 `(venv)` 확인
    4. 추가로 `pip list` 를 통해서 정상적으로 생성되었는지 확인
        1. 설치된 패키지들이 없으면 정상
        2. 설치한 것이 없음에도 패키지들이 많이 있다면 venv 폴더 삭제 후 다시 가상환경 설정
        
6. 장고를 설치한다. (필요한 패키지를 설치한다.)
    1. `pip install django==3.2` 
    2. 만약 `requirements.txt` 가 제공된다면
        1. `pip install -r requirements.txt`   → 기억 필수
        
7. `requirements.txt` 파일을 생성한다.  (잊지말자!)
    1. 패키지의 목록을 버전과 함께 작성해두는 파일
    2. `pip freeze > requirements.txt`
    
8. 모든 설치가 끝났으니 프로젝트를 생성하자
    1. `django-admin startproject 프로젝트명 .`
        1. 마지막에 `.` 이 있는 경우는 현재 폴더에 바로 파일을 생성
        2. `.` 이 없으면 프로젝트명으로 폴더를 만들고 그 내부에 파일을 생성
        
9.  장고 application을 생성한다.
    1. `python [manage.py](http://manage.py) startapp 앱이름`
        1. 앱이름은 복수형으로 작성하는 것을 권장
    2. `[settings.py](http://settings.py)` 내부에 방금 생성한 앱을 등록해야한다.
        1. `INSTALLED_APP` 리스트 내부에 어플리케이션 이름을 문자열형태로 등록해준다.
        2. 주의) `,` 빠지지 않도록 신경을 써주세요!!!


# 구조

## 프로젝트 구조
- __init_.py
  - Python 에게 이 디렉토리를 하나의 Python 패키지로 다루도록 지시
  - 별도로 추가 코드를 작성하지 않음
- settings.py
  - Django 프로젝트 설정을 관리
- urls.py
  - 사이트와 url과 적절한 views의 연결을 지정
- manage.py
  - Django 프로젝트와 다양한 방법으로 상호작용하는 커맨드라인 유틸리티

> 애플리케이션 생성
  - $ python manage.py startapp articles

## 애플리케이션 구조
- admin.py
  - 관리자용 페이지를 설정 하는 곳
- models.py
  - 애플리케이션에서 사용하는 Model(데이터 구조)를 정의하는 곳
  - MTV 패턴의 M에 해당
- tests.py
  - 프로젝트의 테스트 코드를 작성하는 곳
- views.py
  - view 함수들이 정의 되는 곳
  - MTV 패턴의 V에 해당


> 앱을 사용하기 위해 반드시 INSTALLED_APPS 리스트에 반드시 추가해야 함

```python
# setting.py

INSTALLED_APPS = [
    'articles'
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

```


## 요청과 응답
- Django의 세가지 구조
  - Model
  - View
  - Template

- URL -> VIEW -> TEMPLATE 데이터 흐름 이해하기

# Django`s Design pattern
- Django에도 이러한 디자인 패턴이 적용이 되어 있는데, Django에 적용된 디자인 패턴은 MTV 패턴이다.
- MTV 패턴은 MVC 디자인 패턴을 기반으로 조금 변형된 패턴이다.

### MVC 소프트웨어 디자인 패턴
- MVC는 Model - View - Controller의 준말
- 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴
- 하나의 큰 프로그램을 세가지 역할로 구분한 개발 방법론

1. Model : 데이터와 관련된 로직을 관리
2. View : 레이아웃과 화면을 처리
3. Controller : 명령을 model과 view 부분으로 연결

### MVC 소프트웨어 디자인 패턴의 목적
- 관심사 분리 
- 더 나은 업무의 분리와 향상된 관리를 제공
- 각 부분을 독립적으로 개발할 수 있어, 하나를 수정하고 싶을 때 모두 건들지 않아도 됨
  - 개발 효율성 및 유지보수가 쉬워짐
  - 다수의 멤버로 개발하기 용이함

### Django에서의 디자인 패턴
- Django는 MVC 패턴을 기반으로 한 MTV(model-template-view) 패턴을 사용
- 두 패턴은 서로 크게 다른 점은 없으며 일부 역할에 대해 부르는 이름이 다름

## MTV 디자인 패턴
- Model
  - MVC 패턴에서 Model의 역할에 해당
  - 데이터와 관련된 로직을 관리
  - 응용프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리
- Template
  - 레이아웃과 화면을 처리
  - 화면상의 사용자 인터페이스 구조와 레이아웃을 정의
  - MVC 패턴에서 View의 역할에 해당
- View
  - Model & Template과 관련된 로직을 처리해서 응답을 반환
  - 클라이언트의 요철에 대해 처리를 분기하는 역할
  - 동작 예시
    - 데이터가 필요하다면 model에 접근해서 데이터를 가져오고 가져온 데이터를 template로 보내 화면을 구성하고 구성된 화면을 응답으로 만들어 클라이언트에게 반환
  - MVC패턴에서 Comtroller의 역할에 해당

### 정리
- Django는 MTV 디자인 패턴을 가지고 있음
  - Model : 데이터 관련
  - Template : 화면 관련
  - View : Model & Template 중간 처리 및 응답 반환

# Django Template
- 데이터 표현을 제어하는 도구이자 표현에 관련된 로직
- Django Template을 이용한 HTML 정적 부분과 동적 컨텐츠 삽입
- Template System의 기본 목표를 숙지

- Django Template System
  - 데이터 표현을 제어하는 도구이자 표현에 관련된 로직을 담당

## Django Template Language (DTL)
- Django Template에서 사용하는 built-in template system
- 조건, 반복, 변수 치환, 필터 등의 기능을 제공
  - python 처럼 일부 프로그래밍 구조를 사용할 수 있지만 이것은 python 코드로 실행되는 것이 아님
  - Django 템플릿 시스템은 단순히 Python이 HTML에 포함 된 것이 아닌 주의
- 프로그래밍적 로직이 아니라 프레젠테이션을 표현하기 위한 것임을 명심할 것

## DTL Syntax
1. Variable
2. Filters
3. Tags
4. Comments

### variable
- 변수명은 영어, 숫자와 밑줄의 조합을 구성될 수 있으나 밑줄로는 시작 할 수 없음
  - 공백이나 구두점 문자 또한 사용할 수 없음
- dot(.)를 사용하여 변수 속성에 접근할 수 있음
- render()의 세번째 인자로{key:value} 와 같이 딕셔너리 형태로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 Template에서 사용 가능한 변수명이 됨


### Filter
- 표시할 변수를 수정할 때 사용
- 예시
  - name 변수를 모두 소문자로 출력
    - {{variable | filter}}
- chained가 가능하며 일부 일터는 인자를 받기도 함

### Tag
- 출력 텍스트를 만들거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
- 일부 태그는 시작과 종료 태그가 필요함 ex: {% if %}{% endif %}

### Comments

- 주석
{# #}

{% comment %} <br>
  여러 줄
  주석 <br>
{% endcomment %}


# Template ingeritance

## 템플릿 상속
- 템플릿 상속은 기본적으로 코드의 재사용성에 초점을 맞춤
- 템플릿 상속을 사용하면 사이트의 모든 공통 요소를 포함하고, 하위 템플릿이 재정의 할 수 있는 블록을 정의하는 기본 'skeleton' 템플릿을 만들 수 있음
- 만약 모든 템플릿에 부트스트랩을 적용하려면 어떻게 해야 할까?
  - 모든 템플릿에 부트스트랩 CDN을 작성해야 할까?

## 템플릿 상속에 관련된 태그

> {% extends '' %}
- 자식템플릿이 부모 템플릿을 확장한다는 것을 알림
- 반드시 템플릿 최상단에 작성 되어야 함(2개 이상 사용할 수 없음)

> {% block content %}{% endblock content %}
- 하위 템플릿에서 재지정 할 수 있는 블록을 정의
- 즉, 하위 템플릿이 채울 수 있는 공간
- 가독성을 높이기 위해 선택적으로 endblock 태그에 이름을 지정할 수 있음

## 정리
- 공통된 양식이 있는 경우 body.html을 프로젝트 폴더에 탬플릿 폴더 만들자 
- 그리고 각각의 앱에서 프로젝트 폴더에 있는 바디를 참조
  > 템플릿 상속
  1. 프로젝트의 setting에 있는 TEMPLATES 접근
  2. DIRS : [BASE_DIR / 'templates']
    - BASE_DIR : 최상위 폴더
    - 최상위 폴더의 templates라는 폴더를 참조하겠다라는 뜻
    - 해당 프로젝트의 모든 앱에서 블록 사용 가능
  
- 앱이 많을때  각 app에 urls를 관리하자
- why ? 프로젝트 urls에서 다 관리하면 가독성이 떨어지고 프로그램 유지보수에 좋지 않음
  > url 매핑
  1.  각각의 app 폴더안에 urls.py를 생성
  2.  기존 프로젝트 urls 파일의 양식 가져오기 (필요없는 부분 지우고)
  3.  from . import views (현재 앱에있는 views를 import 하겠다는 뜻)
  4.  urlspatterns에 path('index/', views.index) 작성



# Trailing slashes
- Django는 URL 끝에 /가 없다면 자동으로 붙여주는 것이 기본 설정
  - 그래서 모든 주소가 '/'로 끝나도록 되어있음
