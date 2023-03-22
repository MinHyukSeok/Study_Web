# Admin site

- 관리자 페이지
  - 사용자가 아닌 서버의 관리자가 활용하기 위한 페이지
  - 모델 class를 admin.py에 등록하고 관리

```
$ python manage.py createsuperuser
```

### admin에 모델 클래스 등록

```python
# articles/admin.py

from django.cotrib import admin
from .models import Article

admin.site.register(Article)

```

### Article Model 작성
```python
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField

```


# HTTP Method
- GET : 어떠한 데이터를 조회하는 요청
- POST : 어떠한 데이터를 생성하는 요청
- DELETE : 삭제하고자 하는 특정 글을 조회 후 삭제해야 함