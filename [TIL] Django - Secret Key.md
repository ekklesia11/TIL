# [TIL] Django - Secret Key

---

자바스크립트에서 시크릿 키를 가져오는 것처럼 생각하면 안된다. 장고에서는 파일을 읽고 다시 한번 사용 가능하도록 변수에 담아주어야 사용이 가능하다.

장고에서 생성한 앱 폴더 안에 secrets.json 이라는 파일을 만들고 그 안에 객체 형태로 넣어주었다.

```json
{
		"SECRET_KEY": "your_secret_key"
}
```



```python
# myfile.py
from django.core.exceptions import ImproperlyConfigured

# 시크릿 키가 담긴 파일 불러오는 함수
with open("secrets.json") as f:
    secret = json.loads(f.read())

# 시크릿 키를 변수 담을 수 있도록 리턴하는 함수
def get_secret(setting, secret=secret):
    try:
        return secret[setting]
    except:
        error_msg = "Set key '{0}' in secret.json".format(setting)
        raise ImproperlyConfigured(error_msg)

SECRET_KEY = get_secret("SECRET_KEY")
```

이렇게 하면 따로 환경변수라고 지정하지 않아도 외부 파일에 저장된 시크릿 키를 사용할 수 있다.

> *.gitignore* 에 무조건 시크릿 키 경로를 넣어서 원격저장소에 올라가지 않도록 주의하자!

