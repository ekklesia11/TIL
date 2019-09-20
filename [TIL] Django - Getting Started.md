# [TIL] Django - Getting Started

---

## 1. Installation

파이썬이라는 언어가 생각보다 버전에 민감한 듯하다. 파이썬의 버전마다 어떤 버전의 장고를 설치할지 결정해야 하고 그에 따라 프로젝트 환경이 달라지기 때문이다. 조금 더 쉽게 말하면, 각각의 프로젝트마다 그에 맞는 파이썬과 장고 버전을 설치 했을텐데 장고의 파일 이름 등 버전에 상관없이 같은 이름이나 명령어로 동작하기 때문에 분명 이슈가 발생될 것이다. 그래서 가상 환경(virtual environment)을 설정해서 프로젝트마다 독립적인 작업환경을 만들어 그에 맞는 파이썬과 장고 버전을 설치하고 작업할 수 있도록 도와준다.

### Virtual Env 및 Django 설치 

1. 파이썬3 가 제대로 설치 되어 있는지 확인한다. 만약 되어 있지 않다면 공식 홈페이지나 홈브루를 이용해 설치가 가능하다.

   ```bash
   $ python3 --version
   Python 3.7.3
   
   // install python3
   $ brew install python3
   ```

2. 가상환경을 설치할 장소를 선택에 이동하고 (어디든 편한 곳에 - 개인적으로 홈 디렉토리에 폴더를 만들어줬다.) 가상환경을 담을 폴더를 만들어 준다. 이름은 자유롭게 설정. 

   ```bash
   $ cd ~
   $ mkdir virtualenv
   $ cd virtualenv
   ```

3. 파이썬3 버전을 예시로 설치를 진행해본다.

	```bash
	$ python3 -m venv myvenv
	```

4. 아래 명령어로 가상 환경을 실행(activate) 하면 설치한 가상 환경의 이름이 괄호로 감싸져 앞에 보이게 된다. 가상 환경의 이름은 프로젝트마다 원하는 이름으로 설치하면 된다. 그럼 이제 독립적인 환경이 만들어졌다.

   ```bash
   $ source myvenv/bin/activate
   (myvenv) ~
   ```

5. 장고 설치를 위해 pip 버전이 최신 버전인지 확인하고 설치를 진행한다.

   ```bash
   (myvenv) ~$ python3 -m pip install --upgrade pip
   (myvenv) ~$ pip install django~=2.2.0
   
   // version check
   (myvenv) ~$ django-admin --version
   2.2.5
   ```

6. 이제 설치는 완료 됐다. 그러면 파이썬에서 장고를 가져와서 사용할 수 있는 확인해 보자.

   ```bash
   $ python3
   Python 3.7.3 (v3.7.3:ef4ec6ed12, Mar 25 2019, 16:52:21)
   [Clang 6.0 (clang-600.0.57)] on darwin
   Type "help", "copyright", "credits" or "license" for more information.
   >>> import django
   >>> print(django.get_version())
   2.2.5
   ```

