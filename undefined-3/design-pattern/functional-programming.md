# Functional Programming

### 1.Reduce 

각각의 요소를 하나하나씩 접근하는 효과를 줄 수 있지만, 가독성측면에서 강력하다.

```javascript
const numbers = [10, 20, 30, 40];
const sum = numbers.reduce((tot, val) => tot + val);
```

0idx부터 배열을 순회하며 하나하나 다 더해준다 .

뿐만아니라 단순히 코드를 한줄로 작성하는 것이 아닌, map과 filter로 각각 두번해야 하는 연산을 한번의 코드로 사용할 수 있다.

단순히 숫자만 더하는 것이 아닌 평균도 구해보자

```javascript
const avg = numbers.reduce((tot, val, idx, arr) => {
  tot += val;
  if (idx === arr.length - 1) {
    //inx는 0부터 lenth는 1부터 시작하기 때문에 arr의 끝에 도달한 의미
    return tot / arr.length;
  } else {
    return tot;
  }
});
```

### 2.Reduce를 통해 각각 배열요소를 순회하며, 더하거나, 로직을 수행할때 조건을 추가해 견고한 로직을 만들기

```javascript
"use strict"
const numbers2 = [0, 1, 2, 3, 4, 5, 6];

const res = numbers2.reduce((tot, amt) => {
  if (amt > 0) tot.push(amt); //0보다 크면
  return tot;
}, []); //[]에 추가한다.

console.log(res); //[1,2,3,4,5,6] 0보다 크다는 조건때문
```

reduce를 사용하면 한번만 순회해서 코드를 만들 수 있는데,

map이나 filter면 두번이상 사용해야 하는 로직을 1번으로 간소화 할 수 있다 .

### 또다른 예제

실제로 파일 타입을 필터링하는데, 파일타입을 받다보면 중복될 수도 있는데, reduce를 사용해 한번에 알수 있다.

```javascript
const arr = ["pdf", "html", "html", "gif", "gif", "gif"];

const res = arr.reduce((cnt, filrType) => {
  cnt[filrType] = (cnt[fileType] || 0) + 1;
}, {});
//cnt[filrType] 몇
```

