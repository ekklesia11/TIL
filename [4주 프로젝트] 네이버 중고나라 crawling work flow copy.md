# 네이버 카페 중고나라 crawling work flow / url & key tags
---
## Work Flow
1. DB 에서 카테고리 리스트를 가져온다.

2. 해당 페이지의 페이지를 열면서 데이터를 수집한다.

   https://m.cafe.naver.com/ArticleSearchListAjax.nhn?search.query=카테고리&search.menuid=&search.searchBy=1&search.sortBy=date&search.clubid=10050146&search.option=0&search.defaultValue=&search.page=100

   최대 100 페이지

   *페이지당* 20 아이템

   > 해당 주소에 크롤링하고자 하는 카테고리를 넣고, 최대 100 페이지까지 페이지 파라미터를 바꾸면서 각 아이템 크롤링

   

4. 인코딩시 내부모듈 사용가능 

   ```python
   from urllib import parse
   
   encoded = parse.quote('유모차')
   decoded = parse.unquote(encoded)
   
   >>> print(encoded)
   %EC%9C%A0%EB%AA%A8%EC%B0%A8
   >>> print(decoded)
   유모차
   ```

5. :category 파라미터로 인코딩된 한글 검색어 사용

https://m.cafe.naver.com/ArticleSearchListAjax.nhn?search.query=%EC%9C%A0%EB%AA%A8%EC%B0%A8&search.menuid=&search.searchBy=1&search.sortBy=date&search.clubid=10050146&search.option=0&search.defaultValue=&search.page=100

## Key Tags

```mysql
raw_data : 해당 테이블에 필요한 태그 정리 (당근마켓)

brand : 
# 게시글 제목이나 내용에서 해당 정보수집
article > a > div.article-info > div > span.article-title
article > a > div.article-info > div > span.article-content

model : 
# 브랜드와 마찬가지로 제목이나 내용에서 정보수집
article > a > div.article-info > div > span.article-title
article > a > div.article-info > div > span.article-content

price : 
article > a > div.article-info > p.article-price

url :
# 태그 안의 href 주소
article > a
eg) 'https://www.daangn.com' + href

img_url :
# 태그 안의 img 주소
article > a > div.card-photo > img

market :
'당근마켓' or 'https://www.daangn.com'

location :
# 도(시) / 시 / 구 / 동 까지 확인 가능
article > a > div.article-info > p.article-region-name

posted_at : # 확인불가
is_sold : # 확인불가
```



## 이슈

1. 데이트를 알기 위해서는 각 아이템의 해당 페이지로 이동을 해야하는데 데이트 자체가 1시간전, 1일전, 7일전으로 나오는데 논의 필요
2. 판매여부 확인 불가







확인가능한 부분

해당 아이템 주소

판매여부

썸네일 이미지

타이틀

가격 => 타이틀에 적혀 있으면 확인 가능



확인불가한 부분

지역

큰 이미지

게시글 시기 포스트 날짜

