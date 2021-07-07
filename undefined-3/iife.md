# IIFE \(즉시실행함수\)

## IIFE

즉시 실행함수, 말 그대로 정의되자마자 즉시 실행되는 함수를 말한다.

### 표현

```javascript
(function () {})();
```

위 코드는 크게 두가지로 구분된다. 

* \(\)안에 있는 익명함수 -&gt; 전역scope에 불필요한 변수를 추가하지 않아 코드의 오염을 방지할 수 있으며, IIFE내부로 다른 변수가 접근하는 것을 막을 수 있다. 
* \(\)\(\); 두번째\(\)sms 코드를 해석해 실행해준다. 

```javascript
(function () {
  var lang = "js"; //이 함수는 외부에서 접근이 불가능하다.
})();

console.log(lang); //IIFE외부이기 때문에 오류가 발생한다.
```

표현식을 변수에 할당하기 위해서는

```javascript
var r = (function () {
  var lang = "js";
  return lang;
})();
console.log(r); //js
```

js라는 결과가 출력되었는데, r에는 실행결과\(js\)만 저장된다. 

즉, IIFE자체는 저장되지 않고 함수가 실행된 결과만을 저장하는 것이다. 

