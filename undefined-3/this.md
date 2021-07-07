# this

프론트앤드에서 최 상위 스코프에서 this를 찍어보면 window\(global\)이 나온다. 

node.js에서는 조금 다르다. 

```text
1.
console.log(this);   //{}

2.
function a(){
    console.log(this === global);
}     //true
```

1번에서는 빈 객체가 나왔지만, 

2번에서는 true가 출력되었다. 

이유는 다음과 같다. 

```text
console.log(this === module.exports === {} === exports);
```

그 외에는 일반 JS와 같다. 

