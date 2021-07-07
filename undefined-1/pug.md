# PUG

먼저 app.js를 건들여 볼까요

```text
const express = require("express");

const app = express();

//views폴더를 만들고
app.set("views", path.join(__dirname, "views"));
//views폴더안에 있는 pug 선택
app.set('view engine','pug')

```

### PUG사용법

![](../.gitbook/assets/image%20%2815%29.png)

![](../.gitbook/assets/image%20%2824%29.png)

### PUG-변수

```javascript
const express = require("express");

const app = express();

//views폴더를 만들고
app.set("views", path.join(__dirname, "views"));
//views폴더안에 있는 pug 선택
app.set("view engine", "pug");

app.get("/", (req, res, next) => {
  res.render("index", { title: "Express" });
  //위에 views+ /index. + pug 
  //{}안에 부분은 변수
});
//전역변수 설정
app.get("/", (req, res, next) => {
  res.locals.title = 'Express';
  res.render("index");
});
```

### 파일내 변수

![](../.gitbook/assets/image%20%2812%29.png)

### 반복문

![](../.gitbook/assets/image%20%286%29.png)

### 조건문

![](../.gitbook/assets/image%20%285%29.png)

### 상속

![](../.gitbook/assets/image%20%2820%29.png)

### layout

![](../.gitbook/assets/image%20%2810%29.png)

