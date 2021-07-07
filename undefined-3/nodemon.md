# nodemon

nodemon은 파일에 변화가\(세이브\) 생기면 

자동으로 변화를 감지해서 다시실행해준다.



## 설치

```text
npm install nodemon -g
```

아래 코드를 쓰고 

nodemon index.js를 실행하면 계속 안에 내용을 바꾸고

 저장하면 자동으로 실행된다.

```text
console.log("h");
```

![](../.gitbook/assets/image%20%2821%29.png)

```text
console.log("hello");
```

![](../.gitbook/assets/image%20%2830%29.png)

서버를 내렸다 열지 않아도 자동으로 적용된다.

