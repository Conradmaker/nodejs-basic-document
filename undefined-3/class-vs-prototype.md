# Class vs Prototype

## Prototype

* 어떠한 객체나 함수가 있었을때 기존의 속성들을 그대로 복사해서 새로운 함수나 객체로 반환되는 대상
* 기존의 객체와 함수를 바탕으로 새로운 함수를 만드는데 있어서 기존것을 활용할 틀을 재공한다.

```javascript
"use strict";

function fullstack(back, front) {
  this.back = back;
  this.front = front;

  //arrow function의 this는 global
  fullstack.prototype.getBack = () => this.back; //hoisting을 이용해 set을 선언하기 전에 get사용
  fullstack.prototype.setBack = () => (this.back = back);

  fullstack.prototype.getFront = () => this.front;
  fullstack.prototype.setFront = () => (this.front = front);
}
```

fullstack.prototype.getBack 함수내부의 함수로 정의되어있다

 =&gt; closure =&gt; 

해당하는 함수가 함수 외부의 변수에 의해 접근가능

```javascript
const Fullstack = new fullstack("node.js", "React");
Fullstack.getBack();
Fullstack.getFront();
```

## Class

this와 closure을 명확히 유지해주는 것이 중요하다.

```javascript
class fullstack2 {
  constructor(back, front) {
    //async를 가질 수 없다.
    this.back = back;
    this.front = front;
  }
  getBack() {
    return this.back;
  }
  getFront() {
    return this.front;
  }
  setBack() {
    this.back = back;
  }
  setFront() {
    this.front = front;
  }
}
const Fullstack2 = new fullstack2("node.js", "vue.js");
Fullstack2.getBack();
Fullstack2.getFront();
```

기능상의 차이 , 매커니즘도 동일하지만, 코드의 퍼포먼스 향상, 모듈화 , 유지보수 향상을 위한 작업을 리팩토링이라고 한다.

