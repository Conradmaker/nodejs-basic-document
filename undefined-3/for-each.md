# for each

For Each문은 실무에서 매우 많이 사용된다.

동작은 기본적인 for문과 크게 다르지는 않지만, 코드 가독성에 있어서 더 좋기 때문이다.

단, forEach문 내부에서 실행되는 코드들은 비동기적으로 수행되지 않기 때문에 비동기 처리를 할때는 주의해서 사용해야 한다.



```javascript
"use strict";

const arr = [1, 2, 3];

arr.forEach((item) => console.log(item));
/* result
1
2
3
*/
```



또한 배열을 복사할수도 있다.

```javascript
const arr = [1, 2, 3];
const newArr = [];

arr.forEach((item) => newArr.push(item));
console.log(newArr); 
//result: [1,2,3]
```

물론 spread\(...\) 연산자를 사용하면 쉽게 클론할 수 있다.

