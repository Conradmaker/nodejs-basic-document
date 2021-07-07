# 에러처리

보통 순서는 다음과 같습니다 .

1. app을 만들고,
2. app.set으로 설정들 넣고
3. 공통 미들웨어 넣어주고
4. router들 넣어준뒤
5. error middleware 세팅
6. 포트

에러가 발생하는 에러처리 미들웨어로 보내줘야 하는데, 

* err,req,res,next까지 매개변수가 4개
* 첫번째 err에는 에러에 관한 정보가 담긴다. 
* res.status메서드로 HTTP 상태 코드를 지정 가능하다 \(기본200\)
* 에러 처리 미들웨어를 안 연결해도 익스프레스가 알아서 처리해주긴 한다. 
* 특별한 경우가 아니면 가장 아래에 위치시키자

5번 순서에 해당하는 errormiddleware를 만들어보겠습니다. 

```javascript
//에러 미들웨어 (꼭 인자가 4개여야한다.)
app.use((err, req, res, next) => {
  console.log(err);
  res.send("에러발생!");
});
```

여기서 함수의 인자가 4개인데 꼭 4개를 써야 합니다. 

그리고 항상 라우터의 마지막 순서에 넣어줘야 하기 때문입니다 . 

모든 에러는 err 인자로 들어오게 됩니다. 

에러에도 종류가 404, 500번 등등 많은 에러가있는데, 각기 다르게 보여주고 싶다면 어떻게 해야 할까요

```javascript
app.use((req, res, next) => {
  res.status(404).res.send("404에러");
});

app.use((req, res, next) => {
  res.status(500).res.send("404에러");
});
```

404상태일때 .404에러라고 출력됩니다 .

그러나 , 400번대나 500번대 에러들은 서버의 취약점을 해커들에게 취약점들을 알려주는 격이 될 수도 있기 때문에 다 숨긴뒤 첫번째 방법으로 200번대로 출력되게끔 만들 수 도 있습니다. 

또한 보통의 경우에 에러처리를 할 경우 throw new Error를 많이 사용하셨겠지만, express의 경우에는 다음과 같이 사용합니다 . 

```javascript
const express = require("express");
const path = require("path");

const app = express();
app.set("port", process.env.PORT || 3000);

//middleware
app.use((req, res, next) => {
  try {
  } catch (e) {
    next(e);
  }
});
```

next는 보통 다음 코드로 진행시킨다고 알고 있지만, next\(\)안에 인수가 들어가게 되면 , 에러로 인지되어서 아래부분에 작성한 에러처리 미들웨어로 넘겨줍니다 . 

