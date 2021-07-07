# map, filter

## map

배열 내의 모든 요소에 대하여 주어진 함수를 호출한 결과를 이용해 **새로운** 배열을 반환한다.

```javascript
const a = [1, 2, 3];
const m = a.map((item) => item + 1);
console.log(m); 
//result: [2,3,4]
```

## filter

주어진 함수의 테스트를 통과하는 모든 요소들을 모아 **새로운** 배열을 반환

```javascript
const a = [1, 2, 3];
const f = a.filter((x) => x > 1);
console.log(f); 
//result: [2,3]
```

