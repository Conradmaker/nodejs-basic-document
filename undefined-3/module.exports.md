# module.exports

import 받기 위해서는 exports가 필요한데 

Node.js에서 사용하는 방법은 다음과 같다. 

참고로 React에서는 아래와 같이 사용한다. 

```javascript
export default function app(){}

export const app2=()=>{}
```

## exports

함수를 하나 만들어보면 

```javascript
"use strict";

function edit() {}
```

그뒤 함수를 exports 하게 된다면 다음과 같다.

```javascript
module.exports = edit;
```



## 여러개 exports

놀랍게도 여러개를 객체로 한번에 exports할 수도 있다. 

함수 2개와 클래스1개를 만들어보자.

```javascript
"use strict";

function edit() {}
function write() {}

class update {}
```

exports는 다음과 같이 할 수 있다.

```javascript
module.exports = {
  edit,
  write,
  update,
};
```

위처럼 두가지이상의 함수, 클래스를 export할때는 객체로 export할 수 도 있고, 하나면 단일로 할수도 있다.

## inline-exports

뿐만아니라 인라인으로도 함수를 export할 수 있는데 다음 예시와 같다.

```javascript
module.exports = {
  id: "",
  token: "",
  fn: () => {
    console.log("this is function");
  },
};
```



단일 파일로 module을 export를 하면 외부 환경변수와 같은 데이터를 config file로 엮어 표현하기가 좋다.



한번 읽어온 파일은 캐시에 들어있기 때문에 다음 require에서는 조금 더 빨라집니다 . 

만약 파일 1이 파일2를 참조하고, 파일2가 파일1을 참조하게 되면, 순환참조\(무한\) 가 발생하게 되는데, 

node.js가 빈객체로 만들어서 과부하를 막아줍니다. 



