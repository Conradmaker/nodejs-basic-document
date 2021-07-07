# const, let \(scope\)

var은 함수스코프를 가지고 있다 . 

const, let은 {}스코프를 가지고 있다 . 

```text
const a = 3; 
a= '5' //에러

const b = {name:'conrad'};
b.name = 'wG'; //이건 가능
//즉 const는 직접 대입은 다시 불가능하지만, 내부값은 바꿀 수 있다. 
```

