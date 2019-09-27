# [TIL] Django - Error Cases

---

### 1. 쿼리셋에서 첫번째 인덱스에 접근하기

쿼리셋을 불렀을때 .values() 로 실행시켜주면 리스트와 같은 모양의 쿼리셋이 나온다. 하지만 리스트와 같이 인덱스 넘버로 접근을 하려고 하면 에러를 뱉어준다. 이럴때는 .first() 를 활용하여 첫번째 인덱스의 값을 가져올 수 있다.

또 하나의 방법은 .values() 가져온 쿼리셋은 list(쿼리셋) 으로 감싸서 리스트화 시켜준다. 그러면 인덱스 넘버로 접근이 가능해 진다.



### 2. KoNLPY 수용 타입

코넬파이에서는 utf-8 으로 변환이 안되는 이모티콘이나 \n 등 스트링이 아닌 타입이 들어가면 에러를 발생 시킨다. 이럴 때는 다음과 같은 함수를 쓰면 가능하다.

```python
def convertSpecialCharactersIntoSpace(string):
    newString = re.sub(
        r"[-=+_,#/\?:^$.@*\"※~&%ㆍ!』\\‘|\(\)\[\]\<\>\{\};`'…》\n]", " ", string
    )
    before_emoji_clear = re.compile(
        '[\U00010000-\U0010ffff]', flags=re.UNICODE)
    newString = before_emoji_clear.sub(r'', newString)
    return newString
```

