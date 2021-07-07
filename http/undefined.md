# 쿠키와 세션

쿠키와 세션은 로그인과 로그아웃에 있어서 필수적으로 알아두어야 하는 개념이다. 

RESTapi에서 주소별로 파일을 제공하고, POST,PUT,DELETE를 통해 서버쪽 자원을 수정하는 것을 해보았다면,  이번시간에는 로그인에 대해 알아볼 것이다. 

## 쿠키

### 쿠키의 필요성

#### 요청에는 한가지 단점이 있다. 

* 누가 요청을 보냈는지 알 수 없다. \(ip주소화 브라우저 정보 정도만 알 수 있음\)
* 로그인을 구현하면 됨
* 쿠키와 세션이 필요

#### 쿠키: 키=값의 쌍

* name = conrad
* 매 요청마다 서버에 동봉해서 보냄
* 서버는 쿠키를 읽어 누구인지 파악한다. 

![](../.gitbook/assets/image%20%281%29.png)

### 쿠키 서버 만들기

writeHead: 요청 헤더에 입력하는 메서드 

Set-Cookie: 브라우저에게 쿠키를 설정하라고 명령

아래와 같은 방법으로 서버에서 브라우저로 쿠키를 함께 전달 할 수 있다. 

```javascript
res.writeHead(200, { "Set-Cookie": "mycookie = test" });
```

쿠키를 받은 브라우저는 그 후부터 서버로 쿠키를 함께 전달하게 되는데

아래와 같은 방법으로 요청헤더에 있는 쿠키를 서버에서 읽을 수 있다. 

```javascript
console.log(req.headers.cookie);
```

```javascript
//대충 이런식이다..
http
  .createServer(async (req, res) => {
    try {
      if (req.method === "GET") {
        if (req.url === "/") {
          const data = await fs.readFile("./restFront.html");
          res.writeHead(200, {
            "Content-Type": "text/html; charset=utf-8",
            "Set-Cookie": "mycookie = test",
          });
          return res.end(data);
        }
  });
```

### 헤더와 본문

#### http 요청과 응답은 헤더와 본문을 가진다. 

* 헤더는 요청 또는 응답에 대한 정보를 가진다.
* 본문은 주고받는 실제 데이터
* 쿠키는 부가적인 정보이므로 헤더에 저장된다.

![](../.gitbook/assets/image%20%2826%29.png)

### 쿠키로 나를 식별하기

```javascript
const http = require("http");
const fs = require("fs").promises;
const url = require("url");
const qs = require("querystring");

//문자열을 객체로 바꿔주는 함수
const parseCookies = (cookie = "") =>
  cookie
    .split(";")
    .map((v) => v.split("="))
    .reduce((acc, [k, v]) => {
      acc[k.trim()] = decodeURIComponent(v);
      return acc;
    }, {});

http
  .createServer(async (req, res) => {
    const cookies = parseCookies(req.headers.cookie);
    // 2.주소가 /login으로 시작하는 경우
    if (req.url.startsWith("/login")) {
      //queryString에서 name을 추출
      const { query } = url.parse(req.url);
      const { name } = qs.parse(query);
      const expires = new Date();
      // 쿠키 유효 시간을 현재시간 + 5분으로 설정
      expires.setMinutes(expires.getMinutes() + 5);
      //redirect
      res.writeHead(302, {
        Location: "/",
        "Set-Cookie": `name=${encodeURIComponent(
          name
        )}; Expires=${expires.toGMTString()}; HttpOnly; Path=/`,
        //Expires:유효기간 설정. HttpOnly:JS로 접근을 막는다. Path: /아래 주소는 쿠키사용 가능
      });
      res.end();
      // name이라는 쿠키가 있는 경우
    } else if (cookies.name) {
      res.writeHead(200, { "Content-Type": "text/plain; charset=utf-8" });
      res.end(`${cookies.name}님 안녕하세요`);
    } else {
      // 1.아무것도 없는 경우
      try {
        const data = await fs.readFile("./cookie2.html");
        res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
        res.end(data);
      } catch (err) {
        res.writeHead(500, { "Content-Type": "text/plain; charset=utf-8" });
        res.end(err.message);
      }
    }
  })
  .listen(8084, () => {
    console.log("8084번 포트에서 서버 대기 중입니다!");
  });

```

쿠키를 통해 브라우저가 마련한 안전장치를 이용하도록 하자.

### 옵션들

| 속성 | 기능 |
| :--- | :--- |
| 쿠키명 = 쿠키값: | mycookie = text같이 설정 |
| Expires | 만료기한. 이 기간이 지나면 쿠키가 제거됨. 기본값은 클라이언트 종료시까지 |
| Max-age = 초 | Expires와 비슷하지만 날짜대신 초를 입력 Expires보다 우선순위 |
| Domain | 쿠키가 전송될 도메인을 특정할 수 있다. 기본값은 현재 도메인 |
| Path | 쿠키가 전송될 URL을 특정할 수 있다. 기본값은 '/'이다. |
| Secure | HTTPS일 경우에만 쿠키가 전송 |
| HttpOnly | 자바스크립트에서 쿠키에 접근할 수 없다. 보안을 위해 사용권장 |

하지만 이러한 방법에는 문제가 있는데, 브라우저 개발자도구를 통해 쿠키를 볼수도 있고, 수정도 할 수 있다. 

그래서 우리는 암호화된 정보를 이용해야 하는데 그 방법이 세션이다. 

## 세션

### 쿠키의 정보는 노출되고 수정되는 위험이 있음

* 중요한 정보는 서버에서 관리하고 클라이언트에는 세션 키만 제공
* 서버에 세션객체 생성후, uniqueInt\(키\)를 만들어 속성명으로 사용
* 속성 값에 정보를 저장하고 uniqueInt를 클라이언트에 보냄

```javascript
const http = require("http");
const fs = require("fs").promises;
const url = require("url");
const qs = require("querystring");

const parseCookies = (cookie = "") =>
  cookie
    .split(";")
    .map((v) => v.split("="))
    .reduce((acc, [k, v]) => {
      acc[k.trim()] = decodeURIComponent(v);
      return acc;
    }, {});

//데이터 저장용
const session = {};

http
  .createServer(async (req, res) => {
    const cookies = parseCookies(req.headers.cookie);
    if (req.url.startsWith("/login")) {
      const { query } = url.parse(req.url);
      const { name } = qs.parse(query);
      const expires = new Date();
      expires.setMinutes(expires.getMinutes() + 5);
      //차이점 (키) - 다른사람이랑 겹치면 안된다.
      const uniqueInt = Date.now();
      //세션[키]에 name,시간을 담은뒤
      session[uniqueInt] = {
        name,
        expires,
      };
      res.writeHead(302, {
        Location: "/", 
                    //쿠키 대신에 session을 날려준다. 
        "Set-Cookie": `session=${uniqueInt}; Expires=${expires.toGMTString()}; HttpOnly; Path=/`,
      });
      res.end();
      // 세션쿠키가 존재하고, 만료 기간이 지나지 않았다면
    } else if (
      cookies.session && //세션이 있고
      session[cookies.session].expires > new Date() //만료기간이 지나지 않았다면
    ) {
      res.writeHead(200, { "Content-Type": "text/plain; charset=utf-8" });
      // 세션에서 name을 꺼낸다.
      res.end(`${session[cookies.session].name}님 안녕하세요`);
    } else {
      try {
        const data = await fs.readFile("./cookie2.html");
        res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
        res.end(data);
      } catch (err) {
        res.writeHead(500, { "Content-Type": "text/plain; charset=utf-8" });
        res.end(err.message);
      }
    }
  })
  .listen(8085, () => {
    console.log("8085번 포트에서 서버 대기 중입니다!");
  });

```

브라우저는 의미를 알 수 없는 키를 가지고 있고, 그 키를 통해 서버에서 데이터를 가져오는 것이다. 

express와 함께 진짜 사용법을 나중에 배워보자

