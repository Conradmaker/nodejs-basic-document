# Generator Function

이번에는 프론트앤드 Redux-Saga에서 매우 중요한 요소가되는 Generator입니다 .



### 특징

* yield : 함수의 return과는 다른 yield를 가지고 있다. -데이터를 반환하지만 함수를 끝내지 않고 일시정지 해놓는다.
* Arrow function을 사용하면 안된다.
* function\*을 사용한다.
* next\(\)를 통해 다음 코드로 넘어간다.



제네레이터 함수를 만든뒤

```javascript
"use strict";
function* log() {
  console.log(0, yield);
  console.log(1, yield);
  console.log(2, yield);
}
```

호출을 대입해준다.

```javascript
const gen = log();
```

그뒤 호출을 해주면

```javascript
gen.next("zero"); //0,zero
gen.next("first"); //1,first
gen.next("second"); //2,second
```



그외

```javascript
const obj = {
  *gen() {
    let cnt = 0;
    yield ++cnt;
    yield ++cnt;
    yield ++cnt;
  },
};

const g = obj.gen();

console.log(g.next()); // {value:1, done:false}
console.log(g.next()); // {value:2, done:false}
console.log(g.next()); // {value:3, done:true}

```

