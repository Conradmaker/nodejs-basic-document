# express

익스프레스를 한번 접해보면 다시는 http로 돌아갈 수가 없다..

또한 express가 node에서 가장 안전하고 편안하고 압도적인 점유율을 가지고 있다. 

`npm i express`로 익스프레스를 먼저 깔아줍니다 . 

물론 npm init으로 pakage.json을 만들어 주셔야겠죠.

그 다음은 서버 생성입니다. 

```javascript
//express를 불러온뒤
const express = require("express");
//express를 app으로 호출하고
const app = express();
// '/'url로 접근할때 response로 'hello'를 보내줍니다. 
app.get("/", (req, res) => {
  res.send("hello");
});
// 3000번 포트에서 서버 실행
app.listen(3000, () => {
  console.log("express서버 실행 in 3000");
});
```

이런 식으로도 사용할 수도 있습니다 . 

```javascript
const express = require("express");

const app = express();

//서버에 속성을 심는것 (전역변수개념)
app.set("port", process.env.PORT || 3000);

app.get("/", (req, res) => {
  res.setHeader();
  res.send("hello");
});
//전역변수 사용
app.listen(app.get("port"), () => {
  console.log("express서버 실행 in 3000");
});
```

장점은 분기처리가 필요없으며, get,post와 같은 메소드를 통해 편하게 작성할 수 있습니다.

nodemon같은 경우에는 전에 올린 내용을 활용하면 됩니다. 

아 API 서버와 같은 경우에는 json을 반환해야 하기 때문에, `res.json`을 사용합니다. 

