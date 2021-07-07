# 자주쓰는 미들웨어

* morgan
* cookie-parser
* express-session

body-parser는 더 좋은 기술들이 나왔기 때문에 설명하지 않겠습니다 . 



## morgan

```javascript
const express = require("express");
const path = require("path");
const morgan = require("morgan");
const app = express();
app.set("port", process.env.PORT || 3000);

app.use(margan("dev"));

//middleware
app.use((req, res, next) => {
  try {
  } catch (e) {
    next(e);
  }
});
```

요청/응답을 보냈을때 로그를 찍어주는 미들웨어입니다. 

참고로 dev가 아니라 combined를 끼면, ip,browser등의 정보까지 출력되기 때문에 배포모드에서는 combined를 사용하세요

## cookie-parser

http에서는 매우 복잡했던 cookie express에서 간단히 사용할 수 있습니다 . 

```javascript
const cookieParser = require("cookie-parser");
app.use(cookieParser());
app.get("/", (req, res) => {
  req.cookies; //{mycookie:'test} 알아서 파싱이 된다 .

  //쿠키설정
  res.cookie("name", encodeURIComponent(name), {
    expires: new Date(),
    httpOnly: true,
    path: "/",
  });
  
  //쿠키 지울때
  res.clearCookie("name", encodeURIComponent(name), {
    expires: new Date(),
    httpOnly: true,
    path: "/",
  });
  res.sendFile(path.join(__dirname, "index.html"));
});
```



## body-parser

예전에는 따로 패키지를 설치해줘야 했지만, 이제는 express에 내장되어 있습니다 . 

```javascript
//공통 미들웨어에서 설정해주면
app.use(margan("dev"));
app.use(cookieParser());
app.use(express.json()); //클라이언트에서 json을 보내면 자동 파싱
app.use(express.urlencoded({ extended: true })); //qs사용

//라우터에서 사용할 수 있습니다.  
app.get("/about", (req, res) => {
  req.body.name; //이런식으로 데이터가 들어있다 . 
  res.send("상세페이지");
});
```

## express-static

정적파일에 사용 \(express내장\)

```javascript
app.use(margan("dev"));

//app.use("요청경로", express.static(실제경로));
app.use("/", express.static(__dirname, "publuc")); //public폴더가 있어야함.
// 요청경로 : localhost:3030/hello.css  실제경로:learn-express/public/hello.css

app.use(cookieParser());
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

static에서 만약 실제 이미지나 파일이 존재하면 다음이 실행되지 않기 때문에 앞에다 넣어줍니다. 



## express-session

```javascript
app.use(
  session({
    resave: false,
    saveUninitialized: false,
    secret: "보안키",
    cookie: {
      httpOnly: true,
    },
    name: "connect.sid", //기본값
  })
);

app.get("/", (req, res) => {
  req.session; //자동으로 그 사용자(요청보낸사람)에 대한 세션이 된다
  res.sendFile(path.join(__dirname, "index.html"));
});
```

## 미들웨어 확장법

만약 로그인을 했다면, 정적파일을 보내주고 안했다면 다음 미들웨어로 넘어가게 하고싶다면 미들웨어 확장을 하면 편리하다 . 

예시를 보자 

```javascript
app.use("/", (req, res, next) => {
  if (req.session.id) {
    //session id가 있다면
    express.static(__dirname, "public")(req, res, next); //확장
  } else {
    next(); //없다면 다음 미들웨어로
  }
});
```

CORS, passport등의 패키지에도 미들웨어 확장을 쓸 수 있으니 기억하자

## multer

form 태그의 enctype이 multipart/form-data인 경우

* body-parser로는 요청 본문을 해석할 수 없음
* multer필요

```javascript
<form action='/' method='post' enctype='multipart/form-data'> 
```

위와같은 경우 body-parser로 해석이 불가능하다 . 

직접 할수도 있지만, multer쓰는게 맘편하다~

multer자체가 미들웨어이기 보다는 multer안에 4가지 함수가 미들웨어이다. 

```javascript
//호출
const multer = require('multer')
const fs = require('fs') //폴더찾기위해

//폴더찾기
try{
  fs.readdirSync('uploads');
}catch{
  console.error('uploads폴더가 없어 만들게요');
  fs.mkdirSync('uploads');
}

//호출결과물을 업로드에 담고
const upload = multer({
  storage:multer.diskStorage({ //업로드한 파일을 어디에 저장(하드,메모리,클라우드도 가능(패키지))
    destination(req,file,done){ //어디에 저장할지
      done(null,'uploads/')   //uploads폴더에 (만들어야함)
    },
    filename(req,file,done){
      const ext = path.extname(file.originalname); //확장자추출
      done(null,path.basename(file.originalname,ext)+Date.now()+ext) 
             //파일이름,날짜,확장자 날짜를 올리는이유는 동명파일이2개있을수도
    }
  }),
  limits:{fileSize:5*1024*1024},//파일사이즈,갯수를 설정(5mb이하)
})

//이 upload를 router에 장착시킨다.
app.
```



