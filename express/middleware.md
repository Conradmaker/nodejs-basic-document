# middleware

익스프레스는 미들웨어로 구성되 있습니다 .

* 요청과 응답의 중간에 위치하여 미드루에어 
* app.use\(미들웨어\)로 장착
* 위에서 아래로 실행
* req,res,next가 매개변수인 함수
* req:요청 , res:응답
* next\(\)로 다믕 미드루에어로 넘어감

```javascript
const express = require("express");
const path = require("path");

const app = express();
app.set("port", process.env.PORT || 3000);

app.get("/", (req, res) => {
  res.sendFile(path.join(__dirname, "index.html"));
});

app.listen(app.get("port"), () => {
  console.log("express서버 실행 in 3000");
});
```

위와 같이 get '/' post '/'처럼 주소를 나누어 처리하면 코트가 깔끔해지지만, 나쁜점도 있습니다. 

만약 console.log\('모든요청에 실행'\); 과같은 모든 router에 적용하고 싶은 코드가 있다면 중복 처리가 됩니다. 

middleware사용법을 알아보요. 

```javascript
const express = require("express");
const path = require("path");

const app = express();
app.set("port", process.env.PORT || 3000);

//middleware
app.use((req, res, next) => {
  console.log("모든 요청에 실행");
  next(); //next를 통해 다음 코드로 넘어간다.
});

app.get("/", (req, res) => {
  res.sendFile(path.join(__dirname, "index.html"));
});

app.listen(app.get("port"), () => {
  console.log("express서버 실행 in 3000");
});
```

express는 위에서 아래로 실행되기 때문에 위에서 미들웨어가 한번 걸러주게 됩니다. 

```javascript
app.use((req, res, next) => {
  console.log("모든 요청에 실행");
  next(); 
});
```

이런 미들웨어는 callback부분이 미들웨어이고 ,app.use에 장칙시키는 것입니다. 

또한 연달아 실행시킬 수도 있습니다 .



```javascript
app.use((req, res, next) => {
  console.log("모든 요청에 실행");
  next(); 
},(req, res, next) => {
  console.log("모든 요청에 실행2");
  next(); 
},(req, res, next) => {
  console.log("모든 요청에 실행3");
  next(); 
});
```

아래의 경우도 있습니다. 

```javascript
const express = require("express");
const path = require("path");

const app = express();
app.set("port", process.env.PORT || 3000);

//middleware
app.use((req, res, next) => {
  console.log("모든 요청에 실행");
  next();
});

app.get("/", (req, res) => {
  res.sendFile(path.join(__dirname, "index.html"));
});

app.get("/about", (req, res) => {
  res.send("상세페이지");
});
// * 은 모든 get요청에 대해 실행합니다. 
app.get('*',(req,res)=>{
    res.send('최후의 모든 요청')
})
app.listen(app.get("port"), () => {
  console.log("express서버 실행 in 3000");
});

```

위와 같이 모든 요청에 대해 실행하는 경우는 항상 아래쪽에 위치해야만 합니다 . 



