# File System

node.js 를 사용한다면 어떤 경우일까?

웹서버를 생성해 대량의 request를 실시간으로 처리하기 위함일 것이다.

이러한 단계에서 하드디스크, 원격클라우드의 파일시스템에 접근하는 일은 매우 빈번히 일어나는데, 어떻게 읽고 쓰고 삭제하는지 알아보자.



## readFile\(읽기\)

```javascript
//file system호출
const fs = require("fs");

fs.readFile("test.txt", "utf-8", (err, data) => {
  //(파일명, 인코딩(기본값 utf-8) ,함수)
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

## writeFile \(쓰기\)

```javascript
//file system호출
const fs = require("fs");

const content = "someThing to write";
fs.writeFile("test1.txt", content, (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log("success");
}); //파일명 , 내용 , 성공여부(에러로 확인)
```



두가지를 함께 사용할 수 있는 callBack Promise파일

```javascript
const fs = require('fs');
const {promisfy} = require('util');//비구조화 할당

//promisefy 사용  Promise로 만들어준다 
const read = promisefy(fs.readFile);
const write = promisfy(fs.writeFile);

//동시에 parameter 초기화 
const writeAndRead = async(data='')=>{
    try{
        await write("test.txt",data); //작업이 완료될때까지 기다림
        return await read("test.txt");
    }catch(e){
        console.error(e);
    }
}
```

