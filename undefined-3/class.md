# Class

JavaScript는 멀티패러다임 언어이다. 

그로인해 객체지향 OOP방식으로 코딩할 수도 있고, 

함수형 프로그래밍을 할수도 있으며, 

원래 Prototype기반의 언어이기도 합니다.



최신 ECMA SCRIPT에는 class가 추가되었기 때문에 좀더 쉽게 객체지향프로그래밍을 구현 할 수 있습니다.

node.js 버젼에 따라 다르니 node.green에 접속해 node.js가 지원하는 es버전을 확인해보세요.





클래스는 여러방면에서 사용되지만, 캐시매니저 , DB매니저 를 구현할때 자주 사용한다.

자바와 같이 public, private과 같은 기능은 typescript에서 지원하고 있으며,

환경변수\(한번 읽으면 또다시 읽을 I/O작업이 필요가 없을떄\) Class를 사용하면 좋다.

```javascript
"use strict";

class cacheManager {
  //생성자  (비동기 불가)
  constructor() {
    this.config = [];
  }
}
//선언
const CacheManager = new cacheManager();
```



