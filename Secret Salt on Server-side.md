# Secret Salt on Server-side

---

## Salt 란?

패드워드와 같이 해커들로부터 지켜내야 하는 값들은 Hash Code를 활용해서 암호화 할 수 있다.

```javascript
const crypto = require('crypto');

let hashCode = crypto.createHash('sha256').update(password);
let hashCodedPassword = hashCoded.digest('hex');
```

2의 256제곱의 수만큼 경우의 수를 가지고 있기 때문에 많은 블록체인 기술에서도 활용되고 있다. 서버쪽에서 이렇게 암호화를 할 수도 있는데 여기에 조금 더 복잡하게 만드는 작업을 한다. "salt" 라고 불리는 임의의 값을 패스워드와 함께 해시코드화 시켜준다. 그렇게 되면 해킹으로 알아내기란 사실상 불가능하다.

```javascript
const express = require('express');
const session = require('express-session');
const crypto = require('crypto');

const app = express();

app.use(
	session({
		secret: 'secret-value',
	})
);

app.set('salt-key', 'arbitary-salt-value');

let hashCode = crypto.createHash('sha256').update(password + app.get('salt-key'));
let hashCodedPassword = hashCoded.digest('hex');
```

위와 같은 코드로 **app.set (  key  ,  value  )** 형태로 서버에서만 접근이 가능한 salt 값을 지정해 **app.get(  key  )** 로 불러와 사용할 수 있다. 만약 이 방법보다도 더 은밀하고 비밀스럽게 salt 값을 저장하고 싶으면 서버 컴퓨터 내에 새로운 파일 안에 salt 값을 저장하고 파일을 숨겨둔다. 그리고 서버 파일에서 숨겨진 파일을 불러와 감춰진 salt 값을 이용할 수 있다.

> 주의 할 점 : .gitignore 에 파일을 등록해 외부로 업로드 되지 않도록 한다.

```javascript
secret.js >
const secret = 'secret-salt-value'
module.exports = secret;

server.js >
const secret = require('./secret');
const crypto = require('crypto');

let hashCode = crypto.createHash('sha256').update(password + secret;
let hashCodedPassword = hashCoded.digest('hex');
```

