# Type Checking

JavaScript에서 변수나 상수를 선언할때에는 String에서 살펴본것과 같이 type을 정의하지 않고 Dynamic type이 된다. 

하지만, 우리가 Type에 대해 확인을 하거나 데이터를 변환할 때는 정확한 결과를 예측하기 위해 Type을 체크해야 할 필요가 있다. 

이때는 `Type of`를 사용하면 된다.



먼저 변수들을 선언해주자

```javascript
"use strict";

const string = "node.js";
const array = [];
const obj = {};
const number = 1;
```



### type of

```javascript
console.log(typeof string); //string

console.log(typeof array); //object

console.log(typeof obj); //object

console.log(typeof number); //number
```

> 사실 Array는 Object의 한 종류이다.
>
> Object가 조금 더 넓은 데이터형이고, Array는 그 안에 포함되는 개념이다.

