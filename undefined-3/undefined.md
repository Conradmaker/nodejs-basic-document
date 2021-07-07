# 자료구조

Event loop를 알아보기 전에 자료구조에 대하여 먼저 알아보는 것이 좋다.



## 큐

FIFO \(First In First Out\) 

먼저 입력된 데이터가 먼저 출력된다. 

```javascript
//빈 배열에 순서대로 값을 넣어줬다. 
const queue = [];
queue.push(1);
queue.push(2);
console.log(queue);   //[ 1, 2 ]

//출력
var r = queue.shift(); 
//shift : 첫번째 요소를 반환하고 제거한다.
console.log(r);   // 1
```

결과와 같이 먼저 입력된 1 이 먼저 출력되었다.



## 스택

LIFO \(Last In First Out\)

나중에 입력된 데이터가 먼저 출력된다.

```javascript
//빈 배열에 순서대로 값을 넣어줬다. 
const stack = [];
stack.push(1);
stack.push(2);
console.log(stack);   // [ 1, 2 ]

//출력
var s = stack.pop();
console.log(s);   // 2
```

나중에 입력된 2 가 먼저 출력되었다.

