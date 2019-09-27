# [TIL] Django - Install mysqlclient on Mac

---

사실 아직 명확히 어떤 이유와 에러의 의미는 이해하지 못했으나 장고 서버를 설치 후 mysqlclient 를 인스톨 하면 무지막지한 에러를 뱉어낸다.

> virtual environment 가 activate 되어 있는지 확인한다.

```bash
$ pipenv install mysqlclient
>>> ERROR
```

맥OS 환경과 파이썬 버전, 그리고 설치되어지는 mysqlclient 의 버전에 따라 문제가 발생하는 듯 하다. 구글링과 여러 블로그를 돌아다니면서 확인한 결과, openssl 사용해서 인스톨을 진행하면 문제없이 설치가 진행된다. 보통 맥OS 의 경우에 openssl 이 설치 되어 있을 수 있다. 그럼 에러를 해결해 보자.

```bash
$ brew install openssl
$ LDFLAGS=-L/usr/local/opt/openssl/lib
$ pipenv install mysqlclient
```

