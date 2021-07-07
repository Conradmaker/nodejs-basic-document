# Template String

ES6이전 template String 이 없었을때는 복잡한 방법이 있었는데,

이제는 한 Sting 안에서 변수와 상수 기존의 데이터를 통합해서 사용할 수 있다.

### 사용법

```javascript
`문자열....${JS}문자열` 
```

### 예제

```javascript
"use strict";

const detail = `자세한 내용`;
let str = `node.js`;

str += ` 공부 내용 ${detail}`;
// node.js 공부 내용 자세한 내용 
//`node.js`+ `공부내용` + `자세한 내용`

const int = 1;
str = `${str}의 값은 무엇입니다.${int}`;
//node.js공부내용자세한 내용의 값은 무엇입니다.1
```



