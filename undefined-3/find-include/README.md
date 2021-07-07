# find , include

## find 

* 설정된 배열에 대해 특정한 요소를 찾을 수 있다. 



## include  

* 설정된 배열에 해당하는 조건에 걸어 그 조건이 해당하면 true ,아니면 false반환



## 사용

먼저 배열을 선언해줍니다.

```javascript
const arr = ["node.js", "React"];
```

### find

```javascript
const ret = arr.find((key) => key === "React");
//값을 반환하기 때문에 새로운 변수에 할당하거나 바로 사용해야 한다.
console.log(ret); //result : React
```

### include

```javascript
const res = arr.include((key) => key === "node.js");
console.log(res); //result: true
```

### 예제

```javascript
for (const item of arr) {   //배열의 item마다
  if (arr.includes(item)) { //item이 있으면
    console.log(item);      //item값을 출력
  }
}
```

> 조건을 계산하기 위해서는 include를 사용해야 한다.
>
> find를 사용하면, 값이 할당은 되었지만 사용되지 않은 변수로 남기때문에
>
> 메모리누수에 악영향을 끼친다.

