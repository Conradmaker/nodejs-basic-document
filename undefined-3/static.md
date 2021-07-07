# Static

## Static method

```javascript
"use strict";

//클래스 생성
class test {
  //생성자
  constructor() {
    this.config = {};
  }

  //일반 method
  fn() {}

  //static method
  static call() {
    console.log("static method입니다.");
  }
}

test.call();  //result: static method입니다.
```

static method 는 클래스를 생성하지 않고 바로 접근해 사용할 수 있다.



#### 그렇다면 어떻게 클래스를 초기화도 안하고 접근할 수 있을까?

생성자에 접근하지 않고 바로 static method를 호출하기 때문이다.

즉 , constructor에 접근할수 없다. 즉, 사용할 수 없는 것이다 .

그 이유는 다음과같다 . 

원래는 아래와 같이 클래스를 호출하지만,

```javascript
const Test = new Test();
```

static은 생성하지 않고 바로 아래와 같이 호출할 수 있다.

```javascript
test.call();
```

그래서 constructor는 의미가 없어진다.

