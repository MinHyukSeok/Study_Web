# Substituting a custom User model

### AUTH_USER_MODEL
- 프로젝트에서 User를 나타낼 때 사용하는 모델
- 프로젝트가 진행되는 동안 변경할 수 없음
- 프로제트 시작 시 설정하기 위한 것이며, 참조하는 모델은 첫 번째 마이그레이션에서 사용할 수 있어야 함

- 다음과 같은 기본 값을 가지고 있음

``` python
# setting.py

AUTH_USER_MODEL = 'auth.User'
```
### how to subtituting a custom User model
- AbstractUser를 상속받는 커스텀 User 클래스 작성
```python
# accounts/models.py

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

- Django 프로젝트에서 User를 나타내는데 사용하는 모델을 방금 생성한 커스텀 User 모델로 지정
``` python
# setting.py

AUTH_USER_MODEL = 'accounts.User'
```
- admin.py에 커스텀 User 모델을 등록
  - 기본 User 모델이 아니기 떄문에 등록하지 않으면 admin site에 출력되지 않음
```python
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```



# HTTP
## HTTP 특징
1. 비 연결 지향(connectionless)
  - 서버는 요청에 대한 응답을 보낸 후 연결을 끊음
    - 예를 들어 우리가 네이버 메인 페이지를 보고 있을 때 우리는 네이버 서버와 연결되어 있는 것이 아님
    - 네이버 서버는 우리에게 메인 페이지를 응답하고 연결을 끊은 것
2. 무상태(stateless)
  - 연결을 끊는 순간 클라이언트와 서버 간의 통신이 끝나며 상태 정보가 유지되지 않음
  - 클라이언트와 서버가 주고받는 메세지들은 서로 완전히 독립적


## 쿠키
- HTTP 쿠키는 상태가 있는 세션을 만들도록 해 줌
- 서버가 웹 브라우저에 전송하는 작은 데이터 조각
- 사용자가 웹사이트를 방문할 경우 해당 웹사이트의 서버를 통해 사용자에 설치되는 작은 기록 정보 파일
  - 브라우저 클라이언트는 쿠키를 로컬에 KEY-VALUE의 데이터 형식으로 저장
  - 이렇게 쿠키를 저장해 놓았다가, 동일한 서버에 재요철시 저장된 쿠키를 함께 전송
- 쿠키는 두 요청이 동일한 브라우저에서 들어왔는지 아닌지를 판단할 때 주로 사용됨
  - 이를 이용해 사용자의 로그인 상태를 유지할 수 있음
- 즉, 웹 페이지에 접속하면 웹 페이지를 응답한 서버로부터 쿠키를 받아 브라우저에 저장하고 클라이언트가 같은 서버에 재요청 시마다 요청과 함께 저장해 두었던 쿠키도 함께 전송

## 세션
- 사이트와 특정 브라우저 사이의 "stage(상태)" 를 유지시키는 것
- 클라이언트가 서버에 접속하면 서버가 특정 session id를 발급하고, 클라이언트는 session id를 쿠키에 저장
  - 클라리언트가 다시 동일한 서버에 접속하면 요청과 함께 쿠키를 서버에 전달
  - 쿠키는 요청 때마다 서버에 함께 전송 되므로 서버에서 session id를 확인해 알맞은 로직을 처리
- session id 는 세션을 구별하기 위해 필요하며, 쿠키에는 session id 만 저장


## Sessiong in Django
- Django는 database-backed sessions 저장 방식을 기본 값으로 사용

## Login
- 로그인은 Session을 Craate하는 과정

## logout
- 로그아웃은 Session을 Delete하는 과정