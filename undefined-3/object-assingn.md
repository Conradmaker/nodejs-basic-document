# object assingn

## object assingn

* assingn :  할당을의미한다.

object assingn은 실재로 새로운 객체를 만들기도 하고, 

두개의 객체를 합쳐서 하나의 객체로 만드는 기능도 있다.



## 사용

### 객체 초기화

```javascript
"use strict";

const ojb = {
  title: "node.js 쉽다.",
};

const newObj = {
  name: "node.js 재미있다.",
};
```

이 객체를 하나로 합치키 위해서는 어떻게 해야 할까?

```javascript
const result = Object.assign({}, obj, newObj); 
//{} 에 obj와 newObj를 합친다.
console.log(result);
```

### spread문법

Object.assign과 같은 기능을 기지지만 spread문법을 사용하는 이유는

가독성적인 측면에서 좀더 쉽게 즉, 직관적으로 코드를 이해할 수 있기 때문이다.

```javascript
const ret = {
  ...ojb,
  ...newObj,
};
console.log(ret);
// result : {title: 'node.js쉽다' , name: 'node.js재미있다'}
```



또한 spread연산자는 객체 뿐만 아니라 배열\(Array\)에도 사용할 수 있다는 장점이있다.

