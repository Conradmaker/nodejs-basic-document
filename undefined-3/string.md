# String

앞에서 배운 template String은 다른 데이터 타입들도 모두 다룰 수 있지만, 

String은 오직 문자열을 위한 메소드 이다. 



우리는 JavaScript에서 String을 따로 선언하지 않고 사용합니다. 

그 이유는 JavaScript는 특정한 데이터의 타입을 선언하지 않는 언어이기 때문인데,

우리가 선언을 하는 변수들은 v8엔진에 의해서 타입이 동적으로 정의되게 된다. =&gt; Dynamic Type 

즉, 우리는 변수를 정의할 때 그 값이 후에 변할것인지, 변하지 않을것인지만 고려하면 되는 것이다. 



## String사용

우리는 이미 String을 사용하고 있다. 

```javascript
let string = 'node.js 짱짱';  
```

이렇게 문자열데이터는 자동으로 String이다 .



이번에는 크게 다음 세가지를 알아볼 것이다. 

* 어떤 문자로 시작하는지
* 특정 문자를 포함하는지 
* 어떤 문자로 끝나지는지

### startsWith\(\)

어떤 문자로 시작하는지를 알아내는 매소드

```javascript
let string = 'node.js 짱짱';  

let isStartWith = string.startsWith("n"); //true
```

### includes\(\)

특정 문자를 포함하는지 알아내는 매소드

```javascript
let string = 'node.js 짱짱';  

let isInclude = string.includes("js"); //true
```

### endWith\(\)

어떤 문자로 끝나는지를 알아내는 매소드

```javascript
let string = 'node.js 짱짱';  

let isEndWith = string.endsWith("짱"); //true
```



> 참고로 자바스크립트는 유니코드를 지원하기 때문에 
>
> 한글이나 형변환과 같은 부분에서 수월하게 사용할 수 있다.



### 위 3가지가 모두 맞는지 검사

```javascript
const checkIfContains = ()=>{
    if(isStartWith && isInclude && isEndWith){
        return true
    }
}

const ret = checkIfContains();
console.log(ret);  //true
```

