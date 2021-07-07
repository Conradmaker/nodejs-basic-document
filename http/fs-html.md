# fs로 HTML읽어 제공

```javascript
const http = require("http");

const server = http
  .createServer((req, res) => {
  //이부분
    res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
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

server2.html /server2.js를 만들어주세요

```javascript
const http = require("http");
const fs = require('fs').promises;

const server = http
  .createServer((req, res) => {
    try {
      res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
      const data = await fs.readFile('./server2.html')
      res.end(data);
    } catch (e) {
      res.writeHead(200, { "Content-Type": "text/plain; charset=utf-8" });
      res.end(err.message);
    }
   
  })
  .listen(8080, () => {
    //8080포트에 연결 성공하면 아래 코드를 실행
    console.log("8080포트에서 서버 대기중");
  });

server.on("error", (error) => {
  console.log(error);
});

```



