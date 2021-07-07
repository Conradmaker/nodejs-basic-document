# https, http2

## https

요청보낼때 헤더에 중요한 정보들이 너무 많이 담겨지기 때문에 탈취되면 위험하다. 

그래서 요청을 암호화해서 전달하기 위해 사용된다. \(암호는 매우 강력하다\)

### 웹서버에서 SSL 암호화를 추가하는 모듈

* 오고 가능 데이터를 암호화해서 중간에 다른 사람이 요청을 가로채더라도 내용을 확인할 수 없다.
* 요즘에는 https 적용이 필수이다. \(개인정보가 있는 곳은 특히 더\)

### https 서버

* http 서버를 https서버로 

  * 암호화를 위해 인증서가 필요한데 발급받아야 한다. 

* createServer가 인자를 두 개 받음

  * 첫번째 인자는 인증서와 관련된 옵션 객체
  * pem,crt,key 등 인증서를 구입할 때 얻을 수 있는 파일 넣기
  * 두 번째 인자는 서버 로직

```javascript
const https = require("https");
const fs = require("fs");

https
  .createServer(
    //이부분이 추가
    //인증기관에서 발급이 가능하며 , 또한 이경우는 서버를 실행할때 한번만 초기화 하기 때문에 Sync를 사용해도 된다.
    //let's encryps 에서 무료로 발급받을 수 있다.
    {
      cert: fs.readFileSync("도메인 인증서 경로"),
      key: fs.readFileSync("도메인 비밀키 경로"),
      ca: [
        fs.readFileSync("상위 인증서 경로"),
        fs.readFileSync("상위 인증서 경로"),
      ],
    },
    // ----------------------------------
    (req, res) => {
      res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
      res.write("<h1>Hello Node!</h1>");
      res.end("<p>Hello Server!</p>");
    }
  )
  .listen(443, () => {
    console.log("443번 포트에서 서버 대기 중입니다!");
  });

```

## http2

### SSL 암호화와 더불어 최신 HTTP/2를 사용하는 모듈

* 요청 및 응답 방식이 기존 http/1.1보다 개선됨
* 웹의 속도도 개선됨

![](../.gitbook/assets/image%20%2827%29.png)

동시성을 늘려 요청을 여러개 보낼 수 있다. 

특히 작은 이미지 수백개가 있다면 속도가 매우 빠르다. 

```javascript
const http2 = require('http2');
const fs = require('fs');

http2.createSecureServer({
  cert: fs.readFileSync('도메인 인증서 경로'),
  key: fs.readFileSync('도메인 비밀키 경로'),
  ca: [
    fs.readFileSync('상위 인증서 경로'),
    fs.readFileSync('상위 인증서 경로'),
  ],
}, (req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  res.write('<h1>Hello Node!</h1>');
  res.end('<p>Hello Server!</p>');
})
  .listen(443, () => {
    console.log('443번 포트에서 서버 대기 중입니다!');
  });
```

개발할때는 http를 쓰다가 실무에서 http2로 수정만 해줘도 된다. 

