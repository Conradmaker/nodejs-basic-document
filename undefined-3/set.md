# set

개발을 하다보면 

방대한 데이터속에 중복되지 않고 한개의 데이터만 

수집하고 싶은 경우가 많이 있다. 

이때 우리는 set을 사용한다.

### 입력\(add\)

```javascript
"use strict";

const text = new Set(); //set 생성

test.add(1);      //순서대로 중복된 값을 넣어줬다.
test.add(1);
test.add(2);
test.add(2);
test.add(3);
```

### 순회\(for of\)

for of 로 set의 입력구조를 확인해보자.

```javascript
for (const item of test) {
  console.log(item);
}

//result
// 1,2,3
```

결과를 확인하면 1과 2를 2개씩 넣어줬지만, 중복된 값들이 없어져있다.

### 값 확인\(has\)

```javascript
test.has(2); //true  2가 포함되어있기 때문에
```

## 요약

* set 은 중복되지 않는 자료구조
* add를 통해 데이터를 입력받을 수 있고, 중복되지 않는다
* has를 통해 자료가 있는지 없는지 확인 할 수 있다
* set을 순회하는 방법은 for of 문법이 있다



