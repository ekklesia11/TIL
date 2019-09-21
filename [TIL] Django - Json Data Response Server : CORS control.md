# [TIL] Django - Json Data Response Server / CORS control

---

## How to response to GET request

장고에서 데이터를 json 형태로 내려줄때 두가지 방법을 활용할 수 있다. HttpResponse 와 JsonResponse 를 활용해보자.



### 1. HttpResponse

```python
# myproject/views.py
import json
from django.http import HttpResponse

def responseData(request):
  	fakeData = [
      {'name': 'Daniel', 'age': 24},
      {'name': 'David', 'age': 18},
      {'name': 'Peter', 'age': 32}
    ]
    return HttpResponse(json.dumps(fakeData), content_type='application/json', charset='utf-8')

# myproject/urls.py
from .views import responseData

urlpatterns = [
  	...
  	path('data/', responseData)
]
```



### 2. JsonResponse

```python
# myproject/views.py
from django.http import JsonResponse

def responseData(request):
  	fakeData = [
      {'name': 'Daniel', 'age': 24},
      {'name': 'David', 'age': 18},
      {'name': 'Peter', 'age': 32}
    ]
    return JsonResponse(fakeData, safe=False)
  
# myproject/urls.py
from .views import responseData

urlpatterns = [
  	...
  	path('data/', responseData)
]
```



## How to allow CORS

CORS 를 허용하는 방법에도 미들웨어를 추가하는 방법과 모듈을 쓰는 방법이 있는데, 더 쉽게 활용 할 수 있는 모듈을 써서 CORS 허용을 해보자.



### 1. django-cors-headers module install

```bash
(venv) $ pip install django-cors-headers
```

### 2. Settings

```python
#myproject/settings.py

INSTALLED_APPS = [
  	...
  	'corsheaders',
]

# 여기서 미들웨어의 순서에 유의하자. CorsMiddleware 가 CommonMiddleware 보다 위에 있어야 한다.
MIDDLEWARE = [
  	...
  	'corsheaders.middleware.CorsMiddleware',
  	'django.middleware.common.CommonMiddleware',
  	...
]

CORS_ORIGIN_ALLOW_ALL = True

CORS_ALLOW_CREDENTIALS = True

CORS_ORIGIN_WHITELIST = [
    'http://127.0.0.1:8000',
  	'http://localhost:8000'
]

# 특정 형태를 가진 주소에서 오는 요청을 허용하려면 아래와 같이 정규표현식을 사용해 화이트리스트에 추가할 수 있다.
# CORS_ORIGIN_REGEX_WHITELIST = [
#     r"^https://\w+\.example\.com$",
# ]

```



## Recommended References :

https://pypi.org/project/django-cors-headers/