# Promise.all/race

Promise.all

```javascript
const promise1 = new Promise((resoleve,reject)=>resolve("즉시호출"));
const promise2 = new Promise((res,rej)=>{
    setTimeout(()=>{
        resolve("3초뒤에 호출")
    },3000)
})
```

* promise1 =&gt; 호출되는 시점에서 바로 반환되는 Promise 
* promise2 =&gt; 최소 3000ms 뒤에 실행되는 Promise

```javascript
Promise.all([promise1, promise2]).then((values) => console.log(values));
```

배열안에 있는 모든 promise가 실행이 완요될때까지 기다린다.

여기서 알수있는 사실은 다음과 같다.

* promise1이 즉시실행이지만, promise2도 끝날때까지 기다렸다가 함꼐 출력된다.
* 한가지 이상, 즉 다수의 비동기 작업에 대해 완료를 보장받을 수 있는것이 Promise.all이다.

### promise.race

가장먼저 resolve된 promise가 return된다.

```javascript
const promise3 = new Promise((res,rej)=>{
    setTimeout(()=>{
        res("2000");
    },2000)
})
const promise4 = new Promise((res,rej)=>{
    setTimeout(()=>{
        res("3000");
    },3000)
})
```

```javascript
Promise.race([promise3, promise4]).then((value) => console.log(value)); //1000
```

promise4가 딜레이가 더 작기때문에 더 먼저 끝난 promise4가 출력된다.

