2019-08-15
# Express
---
## Express
> Fast, unopinionated, minimalist web framework for Node.js

```bash
$ npm install express --save
```



### 사용전 주의할 점

Express는 HTTP APIs 구축하는데 심플하고 가벼운 프레임워크다. HTTP 서버를 복잡한 구조없이 간단하게 만들 수 있다. 한가지 주의 할 점은 HTTP 서버만을 자체적으로 포함하고 있어서 HTTPS 서버를 만든다면 아래와 같은 코드가 필요하다.

```javascript
const app = require('express')();
const https = require('https');
const server = https.createServer(app).listen(config.port, () => {
		console.log('Https App started');
});
```



### 서버를 만들어보자!

아주 간단하게 서버를 만들어 열 수 있다.

```javascript
const express = require('express');
const app = express();

app.listen(3000, () => {
		console.log('Live Server at 3000...')
})
```



#### 에러 핸들링

만약 서버에 요청한 라우터가 잘못되어거나 찾을 수 없는 정보라면 아래 코드를 사용할 수 있다.

```javascript
app.use((req, res, next) => {
		res.status(404).send('Sorry, Page not found.')
})
```

