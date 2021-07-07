# express에서 html문서 읽기

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Express.js</title>
</head>
<body>
    <h1>어서와 Express.js는 처음이지?</h1>
</body>
</html>
```

이번에는 위와 같은 html파일을 읽어오는 법을 배워볼 것입니다 . 

fs 다들 아시죠?? 그거 필요가 없습니다..

```javascript
const express = require("express");
//경로처리를 좀더 확실히 하기 위해 path 호출
const path = require("path");

const app = express();
app.set("port", process.env.PORT || 3000);

//get요청을 보냈을때 실행할 것(경로,callback)
app.get("/", (req, res) => {
  //현재 경로에서 index.html
  res.sendFile(path.join(__dirname, "index.html"));
});

app.listen(app.get("port"), () => {
  console.log("express서버 실행 in 3000");
});

```

`res.sendFile()` 을 사용하면 자동으로 fs기능을 수행해 html을 가져와줍니다.

참고로 한개의 router에서 res.send류를 여러번 하게 되면 안됩니다 .  

`ERR_HTTP_GEADERS_SENT` 에러가 발생하게 됩니다 . 

물론 다음장에 배울 middleware도 포함해서 입니다 . 



