# Timer

Timer는 Node.js의 핵심인 Event Loop의 기반이 된다. 

특히 Front-End 개발에 많이 접해볼 수 있는데, 

UI 페이지를 만들때, 몇초뒤에 실행이 되는 코드를 작성할때, 큰 연산을 사용하는 연산을 할때 setTimeOut을 사용한다.

또한 일부러 시간차를 두기 위해 Timer를 사용할 수 있다.



별도로 글로벌 함수이기 때문에 선언과정이 필요없다.



TimeHandler는 수행되는 조건인데, 정확히 정한 시간뒤에 실행되는 것이 아닌 최소지연시간이다.

Event Loop안에서 //Timer가 하나있다면 , 정확히 시간이 흐른뒤 작동하는 것처럼 보일 수 있지만,

여러개의 타이머가 있다면 그 코드가 완료되는 시점은 Node.js가 폴링방법으로 검사하기 때문에,

코드레벨상에서 고려할 수 없는 외부환경 \(cpu등\)에 의해 영향을 받는다.

## setTimeOut

```javascript
"use strict";
const timeoutObj = setTimeout(() => {
  //메모리누수를 막기위해 변수에 할당해준다.
  console.log("first");
}, 1000); //최소 1초되에 실행된다.
```

## setImmediate

```javascript
const immediateObj = setImmediate(() => {
  console.log("second");
});
```

지연시간이 없이 실행되는 것처럼 보이지만,

setTimeOut과 같은조건 \(0ms\)일때에도 외부환경의 영향으로 순서는 랜덤하다.

## setInterval

```javascript
const intervalObj = setInterval(() => {
  console.log("third");
}, 1000);
```



마지막으로 타이머가 필요없다면 다시 비할당해줘야 한다.

```javascript
clearTimeout(timeoutObj);
cleatImmediate(immediateObj);
clearInterval(intervalObj);
```

