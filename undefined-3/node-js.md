# node와 웹브라우저의 JS 차이점

\*Front-End 주목!! \*

F.E에서의 JavaScript와 Node.js에서의 JavaScript에는 차이점이 있다. 

## 차이점 몇가지

### window

```javascript
window.location.href //현재 주소를 불러오는 매소드
```

window라는 글로벌 객체는 브라우저상에서 코딩을 할때 사용하는 객체이다. 

그러나 Node.js는 브라우저에서 작동하는 것이 아니기 때문에 window를 사용할 수 없다.

### Import

F.E

```javascript
import React from 'react';
```

es6 이후의 문법 즉, babel과 같은 기능으로 인해 React를 사용했던 사람들을 자주 사용해 봤을 임포트문이다. 

Node.js

```javascript
const dns = require('dns');
```

Node.js에서는 require라는 내장함수를 사용한다.



## 글로벌 상수 정의 \(Scope\)

### 상수

```javascript
const global = 'global';  
```

const 는 선언된 { } 블록안에서만 사용할 수 있다.

### 변수

let

```javascript
let global;

if (true){
    let global;  //let은 증괄호 (블록) 안에서만 작동한다.
}
```

var

```javascript
var global;
if(true){
    var global //var은 파일 내부 전체에 작동한다.(Hoisting주의)
}
```

