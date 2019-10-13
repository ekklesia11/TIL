# [TIL] Express - express.json() vs body-parser

---

노드 서버에서 아주 유용하게 쓰이는 모듈 중 body-parser 를 대부분 사용할 것이다. Request 가 오면 json 파일을 파싱해주는 모듈이다. 이 모듈을 따로 설치해서 사용했던 이유는 express 4.0 이 릴리즈 되면서 빌트인 미들웨어를 구분된 패키지로 나눴기 때문이었다. 그런데 4.16.0 버전에서 다시 빌트인 미들웨어 함수로 포함 시켰다. 

```javascript
const bodyParser = require('body-parser');

app.use(bodyParser.json());
```

기존에 위와 같이 쓰던 서버코드는 더 이상 필요 없게 됐다. 이제는 express.json() 로 쓰자!

```javascript
const express = require('express');

app.use(express.json());
```

