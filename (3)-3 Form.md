# Django Form

- Django 유효성 검사를 단순화하고 자동화 할 수 있는 기능을 제공

### Django는 form에 관련된 작업의 세 부분을 처리
1. 렌더링을 위한 데이터 준비 및 재구성
2. 데이터에 대한 HTML forms 생성
3. 클라이언트로부터 받은 데이터 수신 및 처리

### Form Class 선언
```python
# articles/forms.py

from django import forms

class ArticleForm(forms.Form):
    title = forms.CharField(max_length=10)
    content = forms.CharField()

```

### Widgets
- 위젯 적용하기

```python
articles/forms.py

class ArticleForm(forms.Form):
    title = forms.CharField(max_length=10)
    content = forms.CharField(widget=forms.Textarea)

```


# Static files
- 파일 자체가 고정되어 있고, 서비스 중에도 추가되거나 변경되지 않고 고정 되어있음
  - 예를 들어, 웹 사이트는 일반적으로 이미지, 자라 스크립트 또는 CSS와 같은 미리 준비된 추가 파일을 제공해야 함


### Static files 구성하기
1. settings.py에서 STATIC_URL을 정의하기
2. 앱의 static 폴더에 정적 파일을 위치하기
   - my_app/static/sample_img.jpg
3. 템플릿에사 static 템플릿 태그를 사용하여 지정된 경로에 있는 정적 파일의 URL 만들기

```html
{% load static %}

<img src="{% static 'sample_img.jpg' %}" alt="sample image">
```