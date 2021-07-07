# Event Emitter

특정 이벤트가 발생했을 때 일괄적으로 특정 코드를 실행할 수 있도록 구조적으로 코드를 작성하는 방법을 제공한다.



```javascript
"use strict ";
//import
const EventEmitter = require("events");
//클래스 생성
class ChatManager extends EventEmitter {}

const chatManager = new ChatManager();

```

## on

addEventListner , reducer , saga느낌

특정한 이벤트가 발생했을때 임의의 이벤트에 대해 선언

```javascript
chatManager.on("join", () => {
  //(특정이벤트 , callBack)
  console.log("new user joined");
});
```

## emmit

dispatch느낌

```javascript
chatManager.emit("join"); 
//특정한 유저가 입장했을때 join이라는 event를 emit하면 위 코드가 실행
```

