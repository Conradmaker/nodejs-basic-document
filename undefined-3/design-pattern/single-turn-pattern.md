# Single Turn Pattern

express의 경우로 비유하자면,

express서버를 초기화할때 환경설정파일을 읽거나, AWS의 SSM스토어에서 환경변수를 로드할 수 있는데,

이러한 환경변수들을 가진 객체를 만들때, 싱글턴 패턴을 사용하지 않으면, 

서버에 대한 요청이 있을때마다 계속해서 설정을 읽는 불필요한 작업이 이루어진다 . 

객체나 데이터에 있어 최초 한번만 사용됨을 보장하기 위해 사용되는 것이 싱글턴 패턴이다.

```javascript
"use strict";

class CacheManager {
  constructor() {
    if (!CacheManager.instance) {
      //캐시매니저에 instance가 없을때만
      this._cache = [];
      CacheManager.instance = this;
    }
    return CacheManager.instance;
  }
}

const instance = new CacheManager();
Object.freeze(instance);
```

