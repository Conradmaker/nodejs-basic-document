# Hoisting

hoisting은 JavaScript에서 Context 특히, 생성 및 실행 단계가 어떻게 동작하는지에 대한 일반적 생각이다. 

즉, 변수 및 함수의 선언은 컴파일 단계에서 메모리에 저장되지만,  그와 반대로

어떤 코드를 실행하기 전에  함수선언을 메모리에 저장하는 특징을 가장 큰 특징이라고 할 수 있다.

그럼 일반적인 경우를 먼저 보자.

```javascript
function say(word) {
  console.log(word);
}

say("hi");
```

위와 같이 선언을 먼저 한뒤 그 뒤에 호출하는 것이 일반적인 특징인데, 

JS가 코드를 실행하기 이전에 함수선언을 메모리에 저장하는 특성 때문이다.



만약 호출하는 위치를 바꾸면 어떻게 될까?

```javascript
say("hi");

function say(word) {
  console.log(word);
}
```

함수를 선언하기 전에 호출했지만, 정상적으로 작동한다. 



하지만, 다른 경우가 있다. 

```javascript
say2(a); //undifined

function say2(word) {
  console.log(word);
}

var a = 1;
```

만약 이런경우라면 var a = 1;에서 var a; 부분 즉, 선언부만 위로 Hoisting되며, 

값이 정해지지 않았기 때문에 undifined가 출력된다.



