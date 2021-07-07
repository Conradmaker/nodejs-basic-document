# Error Handling \(try-catch\)

예외\(Exception\):처리하지 못한 에러

* 노드 스레드를 멈춤
* 노드는 기본적으로 싱글 스레드라 스레드가 멈춘다는 것은 프로세스가 멈추는 것
* 에러처리는 필수

에러 핸들링에서는 try catch구문을 사용할 수 있다.

```javascript
try {
  a;
} catch (e) {
  console.log("Err : " + e);
}
```

try부분의 코드 실행중에 에러가 발생하면 catch에서 에러를 잡아 parameter\(e\)에 에러를 받는다.



연습문제. 

* 정의되있지 않은 a, 즉 첫 라인에서 에러가 작동하는데, 끊기지 않고 두번째라인이 출력되게 만드시오.

```javascript
a;
console.log("a");
```





답.

```javascript
try {
  a;
} catch (e) {}
console.log("a");

```



