# every, some

## every

es6의 최신문법이다. 

배열이 있는데 해당 배열이 어떤 조건에 모두 만족할 경우 true값을 반환한다.

먼저 배열을 만들어준뒤

```javascript
"use strict";
const arr = [2, 3, 4]; //1보다 큰 배열
```

every를 이용해보자.

```javascript
const isBiggerThenOne = arr.every((key) => key > 1); 
// key가 1보다 크면 true

const isBiggerThenOne2 = arr.every((key) => key > 2); 
// key가 2보다 크면 true
```

결과

```javascript
console.log(isBiggerThenOne); 
//true

console.log(isBiggerThenOne2); 
//false  2가 2보다 크지 않다.
```

> FE에서 선택적으로 랜더링할때도 자주 사용된다. 
>
> 회원가입, 회원로그인, 회원추천 모든 조건을 만족했을 경우
>
>  every를 사용하면 if\( && && &&\)보다 쉽게 랜더링할 수 있다.



## some

some 은 JS의 최신 핵심 문법이다.

every와의 차이점은 every는 모든 조건에 대해 만족해야 true지만,

some은 1개 이상의 요소에 만족하면 true를 반환한다.

```javascript
//배열생성
const arr = [2, 1, 0, -1, -2];

const res = arr.some((key) => key < 0); 
//0보다 작은게 1개라도 있으면 true

console.log(res); //true
```

