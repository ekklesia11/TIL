# [TIL] Django - Crawling with python

---

장고에서 크롤링하는 방법이 노드 익스프레스에서 크롤링 하는 방법과 크게 다르지 않다. 먼저 필요한 모듈을 설치하자.

### 1. requests / bs4 install

```bash
# python http request library
(myvenv) $ pip install requests

# python crawling library => BeautifulSoup4
(myvenv) $ pip install bs4
```



### 2. 네이버 급상승 검색어 1~10위 Crawling

```python
import requests
from bs4 import BeautifulSoup

req = requests.get('https://www.naver.com')
html = req.text

soup = BeautifulSoup(html, 'html.parser')
# 크롬에서 소스코드를 열고 원하는 태그 위에서 copy > copy selector 를 하면 쉽게 태그 경로를 얻을 수 있다. 
topKeywords = soup.select('span.ah_k')

# topKeywords 는 리스트 형태로 들어가기 때문에 for 문을 쓸 수 있다.
for i in range(0, 10):
  	print(topKeywords[i].text)
```

