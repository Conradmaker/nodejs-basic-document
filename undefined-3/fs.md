# fs

파일 시스템이 접근하는 모듈이다. 

* 파일/ 폴더생성, 삭제, 읽기, 쓰기 가능
* 웹 브라우저에서는 제한적이었으니 노드는 권한을 가지고 있다. 

파일읽기 예제 

```text
readme.txt

저를 읽어주세요.
```

```javascript
readfile.js

const fs = require('fs').promises;

fs.readFile('./readme.txt',(err,data)=>{
    .then((data)=>{
        console.log(data);            //16진법으로 출력    
        console.log(data.toString()); //글자로 출력
    })
    .catch(err=>{
        throw err;
    });

})
```

파일 생성 예제

```javascript
writefile.js

const fs = require('fs').promises;

fs.writeFile('./writeme.txt','글이 입력됩니다.')
    .then(()=>{
    })
    .catch(err=>{
        throw err;
    });
```

Promise를 이용한 PromiseChain

```javascript
writefile.js

const fs = require('fs').promises;

fs.writeFile('./writeme.txt','글이 입력됩니다.')
    .then(()=>{
    })
    .then((data)=>{
        console.log(data.toString());
    })
    .catch(err=>{
        throw err;
    });
```

