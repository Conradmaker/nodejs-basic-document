# http / https

## HTTP

Hyper Text Protocol 인터넷 문서간에 즉, 여러 링크를 포함한 문서를 교환하는 것

더 쉽게 서버를 만들 수 있는 express프레임워크가 있지만

http기본 모듈의 원리 이해 없이 express를 사용해버린다면,

node.js의 내부적 로직을 간과하는 것이고, Node.js low레벨적인 문제를 맞이하면 곤란해 질 수 있다.



간단한 코드를 작성할 때는 express를 사용하는 것보다는 http 즉, low model이 성능적으로 우수하기 때문에 유리할 수 있다. 

방법. 

```javascript
"use strict"

const http = require("http"); //내장모듈

const server = http.createServer((req,res)=>{
    //결과가 200이라는 코드가 되면 정상임을 의미한다.
    res.statusCode = 200;
    res.setHeader("Content-Type","text/html"); //어떤 타입의 콘텐츠를 response로 보내는지
    res.end("<div>Hello World</div>")//종료를 하고 어떤걸 보낼지 정의 
})

//서버가 위에서 생성되었기 때문에 요청에 대해 listen해야 한다. 
const port = process.env.PORT;
server.listen(port,()=>{
    console.log(`Server running at port ${port}`)
})
```





## HTTPS

Hyper Text Protocol Secure ssl Protocol 이 추가되어서 모든 데이터교류과정이 암호화되어 전송이 된다.

https사용법은 http사용법과 크게다르지 않다.

```javascript
'use strict'

const https = require("https");
const options = {
    hostname: "google.com",//서버의 이름 ip주소가 아닌 실제 유니코드 도메인주소
    port:442 //일반적으로 ssl프로토콜을 사용하는 https포트는 443이며 기본값이다. 
    path:"/login" //hostname뒤에 결합이 되는 url 'google.com' +'/login'
    method: "GET", //crud중 수행할 매소드 (CREATE READ UPDATE DELETE)
}

//요청을 하게되면 response를 받는다 . 
const req = https.request(option,(res)=>{
    //요청한 결과 즉, 서버가 어떤 응답을 보냈는지 res객체에서 얻을 수 있다. 
    console.log(`statusCode:${res.statusCode}`);
    res.on("data",(d)=>{
        //데이터를 받은 것에 대해서 
        process.stdout.write(d);
    })
    req.on('error',(err)=>{
        console.log(err);
    })
})

//마지막에는 종료시켜 메모리누수를 방지해준다. 
req.end();
```

