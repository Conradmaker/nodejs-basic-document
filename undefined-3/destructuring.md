# Destructuring \(비구조화\)

비구조화는 최신 JS에서는 매우 빈번히 사용된다.

선언부에서 비구조화를 사용하면 매우 편리하기 때문이다.

## 구조화와 비구조화

* 구조화: 객체나 배열을 선언하는 과정
* 비구조화 : 선언된 데이터에서 값을 가져오는 것



비구조화할수 있는 대상에는 '객채', '배열' 두가지가 있다.

비구조화를 하기 위해서는 구조화된 자료가 필요하기 때문에 객체를 만들어보자.

```javascript
"use strict";

//구조화
const obj = {
  title: "node.js",
  value: "안녕하세요",
};

//비구조화(es6)
const { title, value } = obj;
```

참고로 비구조화할당 이전의 문법은 다음과 같다. 

```javascript
const title = obj.title;
const value = obj.value;

//비구조화
//const { title, value } = obj;
```

위코드는 같은 의미인데 하나하나 일일이 값에 접근해서 가져와야만 했다.



배열 비구조화

```javascript
const arr = [0, 1, 2];
const [, a, b] = arr; // ,는자릿수를 맞추기 위함이다.
//a: 1, b:2
```

