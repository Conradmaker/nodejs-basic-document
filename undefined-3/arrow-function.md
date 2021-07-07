# Arrow Function

## Arrow Function

화살표함수라고 부르는데, 파이썬, C\#과 같은 언어에서 사용한 람다와 같은 기능을 JavaScript에서도 사용할 수 있다.

### 장점

Arrow Function 은 코드가독성이 높은것 이외에도, 

일반 함수가 가지고 있던 this에 대해 다른 scope를 가지고 있기 때문에 기존의 문제점을 근본적으로 해결할 수 있다.

### 비교

#### 일반함수

```javascript
function add(a, b) {
  return a + b;
}
console.log(add(1, 2)); //3
```

#### Arrow Function

```javascript
const add2 = (a, b) => a + b;

console.log(add2(1, 2)); //3
```

> 기존 함수의 this의 범위와 다르게 
>
> Arrow Function은 자신의 Context를 고려하지 않고 글로벌 객체를 this로한다.
>
> 참고로, 기존함수는 this가 호출될때 정의되는데, 호출한 대상을 가르킨다.



## 합성함수

```javascript
//Curreid Function
//함수형 프로그래밍을 수행하는데 있어서 매우 편리한 요소로써의 아이템이라고 할 수 있다.
//합성함수

//예를들어 쇼핑몰을 운영하는데, 특정회원들에게 할인을 제공하려고 하는데,
//할인율이 회원등급, 이벤트에 따라 모두 다르다.

//일반함수
function getDiscount(price, rate) {
  return price * rate;
}
getDiscount(10000, 0.1); //9000원

//Arrow Function
const getDiscount2 = (price, rate) => price * rate;
//이렇게 되면 운영에 크게 문제는 없지만, 회원레벨이 많아지고, 이벤트도 다양해진다면,
//할인율과 가격이 다양해져 매우 많은 반복되는 함수들이 필요하다.
//즉 분기별로, 너무 많이지는 것이다.

//그렇다면 getDiscount의 문제점 즉, 한번만 비율을 선언하고
//선언된 비율에 대해 다양한 가격을 입력했을때 가격을 얻을 수 있는 함수를 만드세요.
let rate = 0.4;
const getDiscount3 = (price) => price * rate;
console.log(getDiscount3(30000));
//프로그래밍에서 불편함을 느끼고 그걸 해결하는 것은 매우 중요하다.
//혼자 생각하며 디버깅하는 단계를 가지는 것은 매우 중요하다.

//답
const getDiscount0 = (rate) => (price) => rate * price;
//내부적으로 paremeter를 받고 리턴하는게 아닌 그안에서
//Closure를 생성 (내부적으로 접근할수 있는 함수)
const getTenpercentOff = getDiscount0(0.1);

getTenpercentOff(10000);
```

