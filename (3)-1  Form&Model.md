# Sending form data (Client)
## HTML form`s attribute
1. acthon
   - 입력 데이터가 전송될 URL을 지정

2. method
   - 데이터를 어떻게 보낼 것인지 정의
   - HTML form 데이터는 오직 2가지 방법으로만 전송 할 수 있는데 바로 GET 방식과 POST방식
     - GET(엽서) - 누구나 볼 수 있는 데이터를 요청할 때 ex) 검색, 조회
     - POST(편지) - 양이 많거나 중요한 내용을 전달할 때 ex) 로그인, 글쓰기

## HTML input element
   - 사용자로부터 데이터를 입력 받기 위해 사용
   - 핵심 속성 : name
### name
- form을 통해 데이터를 제출했을 때 name 속성에 설정된 값을 전송하고, 서버는 name 속성에 설정된 값을 통해 사용가자 입력한 데이터 값에 접근할 수 있음
- 서버에 전달하는 파라미터(name은 key, value는 value)로 매핑하는 것

## HTTP request methods
   - HTTP
     - HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜
   - 웹에서 이루어지는 모든 데이터 교환의 기초

   - 자원에 대한 행위(수행하고자 하는 동작)를 정의
   - 예시
    - GET, POST, PUT, DELETE

### GET
- 서버로부터 정보를 조회하는데 사용
  - 서버에게 리소스를 요청하기 위해 사용
  - 데이터를 가져올 때만 사용해야 함
  - 데이터를 서버로 전송할 떄 Query String Parameters를 통해 전송
    - 데이터를 URL에 포함되어 서버로 보내짐


### Query String Parameters
- 사용자가 입력 데이터를 전달하는 방법 중 하나로, url 주소에 데이터를 파라미터를 통해 넘기는것
- 이러한 문자열은 앰퍼샌드(&)로 연결된 key=value 쌍으로 구성되며 기본 URL과 물음표로 구분됨
- 예시
  - http://host:port/path?key=value&key=value
- 정해진 주소 이후에 물음표를 쓰는것으로 Query String이 시작함을 알림


<!-- # Retrieving the data(Server)

## 데이터 가져오기
- 모든 요청 데이터는 view 함수의 첫번째 인자 request에 들어있다.
- print를 통해 살펴보기
 -->



# Django Model
## 개요
- Model의 핵심 개념과 ORM을 통한 데이터베이스 조작 이해
- Django는 웹 어플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 계층(모델)을 제공

## Datebase
- 체계화된 데이터의 모임
- 검색 및 구조화 같은 작업을 보다 쉽게 하기 위해 조직화된 데이터를 수집하는 저장 시스템
- Database의 가장 기초적인 키워드에 대해 알아보고 자세한 내용은 추후 Database 시간에 다룰 예정

### 스키마
- 뼈대
- 데이터베이스에서 자료의 구조, 표현 방법, 관계 등을 정의한 구조
### 테이블
- 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
- 관계라도고 부름
1. 필드
    - 속성, 칼럼
2. 레코드
    - 튜플, 행

### PK (primary key)
- 기본 키
- 각 레코드의 고유한 값 (식별자로 사용)
- 기술적으로 다른 항목과 절대로 중복될 수 없는 단일 값
- 데이터베이스 관리 및 테이블 간 관계 설정 시 주요하게 활용 됨

### 쿼리 (Query)
- 데이터를 조회하기 위한 명령어
- 조건에 맞는 데이터를 추출하거나 조작하는 명령어 (테이블형 자료구조에서)

# Model
- Django는 Model을 통해 데이터에 접근하고 조작
- 사용하는 데이터들의 필수적인 필드들과 동작들을 포함
- 저장된 데이터베이스의 구조(layout)
- 일반적으로 각각의 모델은 하나의 데이터베이스 테이블에 매핑
  - 모델 클래스 1개 == 데이터베이스 테이블 1개

### model.py 작성
- 모델 클래스를 작성하는 것은 데이터베이스 테이블의 스키마를 정의하는 것
- 모델 클래스 == 테이블 스키마

```python
# articles/models.py
class Article(models.Model):
  title = model.CharField(max_length=10)
  content = models.TextField()
```
- 각 모델은 django.models.Model 클래스의 서브 클래스
  - 즉, 각 모델은 django.db.models 모듈의 Moder 클래스를 상속받아 구성됨
  - 클래스 상속 기반 형태의 Django 프레임워크 개발
> 프레임워크에서는 잘 만들어진 도구를 가져다가 잘 쓰는 것

### 데이터베이스 스키마
- 지금까지 작성한 models.py는 데이터베이스 스키마를 정의한 것
- 이제 이러한 모델의 변경사항을 실제 데이터베이스에 반영하기 위한 과정이 필요

## Migrations
- Django가 모델에 생긴 변화(필드 추가, 수정 등)를 실제 DB에 반영하는 방법

### Migrations 관련 주요 명령어
1. makemigrations
  - 모델의 변경사항에 대한 새로운 migration을 만들 때 사용
2. migrate
   - makemigrations로 만든 설계도를 실제 데이터베이스에 반영하는 과정
   - 결과적으로 모델의 변경사항과 데이터베이스를 동기화

> 반드시 기억해야 할 migration 3단계
1. models.py에서 변경사항이 발생하면
2. migration 생성
  - makemigrations
3. DB 반영 (모델과 DB의 동기화)
  - migrate





## ORM
- Object-Relational-Mapping
- SQL을 사용하지 않고 데이터베이스를 조작할 수 있게 만들어주는 매개체

### ORM 장단점
- 장점
  - SQL을 잘 알지 못해도 객체지향 언어로 DB 조작이 가능
  - 객체 지향적 접근으로 인한 높은 생산성
- 단점
  - ORM 만으로 세밀한 데이터베이스 조작을 구현하기 어려운 경우가 있음

# QuerySet API
### Database API
- Django가 제공하는 ORM을 사용해 데이터베이스를 조작하는 방법
- Model을 정의하면 데이터를 만들고 읽고 수정하고 지울 수 있는 API 제공

> Article.object.all()

- Article : Model class
- object : Manager
- all : Queryset API

### object manager
- Django 모델이 데이터베이스 쿼리 작업을 가능하게 하는 인터페이스
- DB를 Python class로 조작할 수 있도록 여러 메서드를 제공하는 manager

### Query
- 데이터베이스에 특정한 데이터를 보여 달라는 요청
- 파이썬으로 작성한 코드가 ORM에 의해 SQL로 변환되어 데이터베이스에 전달되며, 데이터베이스의 응답 데이터를 ORM이 QuerySet이라는 자료 형태로 변환하여 우리에게 전달

### QuerySet
- 데이터베이스에게서 전달 받은 객체 목록(데이터 목록, 쿼리 리스트)
  - 순회가 가능한 데이터로써 1개 이상의 데이터를 불러와 사용할 수 있음
- Django ORM을 통해 만들어진 자료형이며, 필터를 걸거나 정렬 등을 수행할 수 있음
- object manager를 사용하여 복수의 데이터를 가져오는 query method를 사용할 때 반환되는 객체
- 단, 데이터베이스가 단일한 객체를 반환 할 때는 QuerySet이 아닌 모델의 인스턴스로 반환됨

### QuerySet API 익히기
- QuerySet API를 활용해 데이터를 생성하고, 읽고, 수정하고 삭제해보기

# CRUD
- Creat / Read / Update / Delete
  - 생성 / 조회 / 수정 / 삭제
- 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능 4가지를 묶어서 일컫는 말

## CREATE
- 첫번째 방법 
    1. article = Article()
       - 클래스를 통한 인스턴스 생성
    2. article.title
       - 클래스 변수명과 같은 이름의 인스턴스 변수를 생성 후 값 할당
    3. article.save()
       - 인스턴스로 save 메서드 호출

- 두번째 방법
  - 인스턴스 생성 시 초기 값을 함께 작성하여 생성
    1. article = Article(title='second', content='django!')
    2. article.save()

- 세번째 방법
  - QuerySet API 중 create() 메서드 활용
    1. Article.object.create(title='third, content='django!')


#### .save()
- saving object
- 객체를 데이터베이스에 저장함
- 데이터 생성 시 save를 호출하기 전에는 객체 id 값은 None
  - id 값은 Django가 아니라 데이터베이스에서 계산되기 때문

## READ
- QuerySet Api method를 사용해 데이터를 다양하게 조회하기
- QuerySet Api method는 크게 2가지로 분류됨
  - Methods that 'return new querysets'
  - Methods that 'do not return querysets'

#### all()
- QuerySet return
- 전체 데이터 조회
``` python
>>>Article.object.all()
```

#### get()
- 단일 데이터 조회
- 객체를 찾을 수 없으면 DoesNotExist 예외를 발생시키고, 둘 이상의 객체를 찾으면 MultipleObjectsReturn 예외를 발생시킴
- 위와 같은 특징을 가지고 있기 때문에 primary key와 같이 고유성을 보장하는 조회에서 사용해야 함
``` python
>>> Article.object.get(pk=1)
```


#### filter()
- 지정된 조회 매개 변수와 일치하는 객체를 포함하는 새 QuerySet을 반환
- get과는 달리 여러 데이터 조회 가능
- 조회된 객체가 없거나 1개여도 QuerySet을 반환


``` python
>>> Article.object.filter(content='django')

>>> Article.object.filter(title='django')
```

#### field lookups
- 특정 레코드에 대한 조건을 설정하는 방법
- QuerySet 메서드 filter(), exclude() 및 get()에 대한 키워드 인자로 지정
- 다양한 built-in lookups는 공식 문서를 참고


``` python
>>> Article.objects.filter(content__contains='dj')
```

## UPDATE
1. 수정하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
2. article 인스턴스 객체의 인스턴스 변수 값을 새로운 값으로 할당
3. save() 인스턴스 메서드 호출

``` python
 article = Article.objects.get(pk=1)

# 인스턴스 변수를 변경
>>> article.title = 'edit'

# 저장
>>> article.save()

# 정상적으로 변경된 것을 확인
>>> article.title
'edit'
```

## DELETE
1. 삭제하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
2. delete() 인스턴스 메서드 호출

``` python
>>> article = Article.objects.get(pk=1)

# delete 메서드 호출 -> 삭제된 값 반환
>>> article.delete()
(1, {'articles.Article' : })

# 1번 데이터는 이제 조회할 수 없음
>>> Article.objects.get(pk=1)
DoesNotExist: Article matching query does not exist.

```