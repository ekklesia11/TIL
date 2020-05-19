# [TIL]MongoDB + Nodejs

---
npm 설치하고 가시죠~~

```bash
npm install mongodb
```

## MongoDB 와 Nodejs

레퍼런스참조: https://www.mongodb.com/blog/post/quick-start-nodejs-mongodb--how-to-get-connected-to-your-database

위 링크에서 몽고디비에서 제공하는 인스트럭션이다. 순서대로만 하면 된다.

사실 어려운건 없다. 하지만 Database Access 와 Network Access 에서 user 아이디와 비밀번호, 그리고 IP Whitelist 에 현 아이피 또는 0.0.0.0/0 (모두 허용)을 해줘야 한다. 처음에 몰라서 헤매었던 기억이 있다...

```javascript
const { MongoClient } = require('mongodb');

async function main(){
    /**
     * 기본 연결 URI. <username>, <password> 과 <your-cluster-url> 를 Database Access 에서 추가한 유저 아이디와 비밀번호로 대체한다. cluster url 은 clusters 탭에서 connection > Connection your application 에 있다.
     * See https://docs.mongodb.com/ecosystem/drivers/node/ for more details
     */
    const uri = "mongodb+srv://<username>:<password>@<your-cluster-url>/test?retryWrites=true&w=majority";
 

    const client = new MongoClient(uri);
 
    try {
        // Connect to the MongoDB cluster
        await client.connect();
 
        // Make the appropriate DB calls
        // 이곳에 원하는 DB 액션을 작성
 
    } catch (e) {
        console.error(e);
    } finally {
        await client.close();
    }
}
```

몽고디비는 기본적으로 비동기적으로 동작하기 때문에 프로미스 형태로 한번 래핑해서 사용하면 매번 부를때마다 클로즈 하지 않고 데이터를 핸들링할 수 있다. 자세한 내용은 다시 다루도록 하겠다. 그럼 이만