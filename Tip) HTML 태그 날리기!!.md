# Tip) HTML <태그> 날리기!!

---

### JavaScript 로 HTML 파일 불러오기

Ajax 의 방법으로 (fetch 나 XMLHttpRequest) HTML 을 불러오면 수많은 태그와 텍스트들로 정신없는 body 가 완성된다.

JSDOM 모듈을 써서 HTML dom 을 가져와 .textContent 로 불러주면 아주 간단히 해결될 수 있다. 하지만 어떤 모듈도 없이 원하는 태그 내에 있는 텍스트들을 모으는 방법이다.

> ##### HTML 페이지를 가져와 스트링이파이(.json())를 해주고 잘라서 그 안에 있는 모든 <태그>형태를 빈 문자로 바꿔준다!

```javascript
const https = require('https');

async function htmlCaller(url) {
  let body = []
  return await https.get(url, (res) => {
    res.on('data', (d) => {
      body.push(d)
    })
    .on('end', () => {
      body = Buffer.concat(body).toString();
      let first = body.indexOf("<article>")
      let last = body.lastIndexOf("</article>")
      return body = body.slice(first, last).replace(/(<([^>]+)>)/gi,"")
    })
  })
}
```

