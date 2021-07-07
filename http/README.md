# http 서버만들기

서버와 클라이언트 

서버와 클라이언트의 관계

* 클라이언트가 서버로 요청\(request\)를 보냄
* 서버는 요청을 처리
* 처리 후 클라이언트로 응답\(response\)을 보냄

```javascript
const http = require("http");

http
  .createServer((req, res) => {
    res.write("<h1>Hello Node!</h1>");
    res.write("<p>Hello Server!</p>");
    res.end("<p>Hello Node!</p>");
  })
  .listen(8080, () => {
    //8080포트에 연결 성공하면 아래 코드를 실행
    console.log("8080포트에서 서버 대기중");
  });
```

![](../.gitbook/assets/image%20%288%29.png)

* https는 443포트를 생략할수 있다.
* http는 80포트를 생략할 수 있다.

도메인 하나에 페이지를 하나만 연결할 수 밖에 없기 때문에, 

다른 포트를 사용하면 다른걸 보여줄 수 있어서 좋다. 

하나의 호스트에서 포트로 인해 여러개의 프로그램을 동시에 연결할 수 있다. 



서버에서도 에러가 날 수 있기 때문에 에러처리까지 해주자

```javascript
const http = require("http");

const server = http
  .createServer((req, res) => {
    res.write("<h1>Hello Node!</h1>");
    res.write("<p>Hello Server!</p>");
    res.end("<p>Hello Node!</p>");
  })
  .listen(8080, () => {
    //8080포트에 연결 성공하면 아래 코드를 실행
    console.log("8080포트에서 서버 대기중");
  });

server.on("error", (error) => {
  console.log(error);
});

```

