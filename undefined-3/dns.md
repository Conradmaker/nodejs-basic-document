# DNS

## DNS 

Domain Named Server

일반적인 웹주소 \(google.com\) 와 같은 문자주소는 사람이 이해하기 쉽게 하기 위한 주소이고,

컴퓨터가 읽기 위한 주소는 숫자인데,

사람을 위한 주소를 컴퓨터 주소로 바꿔주는것이 DNS모듈



```javascript
const dns = require("dns"); //import 

dns.lookup("test.com", (err, address, family) => {
//실제 ip를 확인하고 싶은 주소
  comsole.log(`address:${address}, ${family}`);
}); 
```

family: ip주소버젼 보통 IPv4



```javascript
//IPv4이기 떄문에
dns.resolve4("test.com", (err, addresses) => {
  if (err) throw err;

  const res = JSON.stringify(addresses); //객체가 오기때문에
  console.log(res);

  addresses.forEach((e) => {
    dns.reverse(a, (err, hostname) => {
      if (err) throw err;
      console.log(`reverse for ${a}; ${JSON.stringify(hostname)}`);
    });
  });
});
```

test.com 이기 떄문에 오류가 발생하지만, 다른 도메인으로 해보면 해결된다.

