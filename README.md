# I/O와 프로그래밍 패러다임

## I / O

Input / Output

컴퓨터는 사용자 데이터를 받고 \(input\) , 내보내는 것\(output\)이 기본이다.

Node.js는 일반적인 WAS \(Web Aplication Server\)들에게는 동시성 프로그램에 문제가 있었기때문에 시작되었다. 

또한 Node.js는 Network I/O가 핵심이라고 할 수 있으며 , 

랙이나 에러도 I/O작업에 의해 일어나며 일부분이다.



## 비동기 vs 동기 

### 동기처리

먼저 동기처리란, 하나의 요청이 있다면, 그 요청을 처리하는 대상과 요청하는 대상이 동일하게 될 때까지  기다리는 것을 말한다. 

### 비동기처리 

동기처리와 반대로 일치해질때 까지 기다리지 않는 것을 의미한다. 



* Node.js는 I/O를 효과적으로 관리하기 위해 비동기처리 모델을 체택했다.
* Node.js의 비동기작업은 v8엔진의 Event Loop에 의해 작업이 이루어진다.

## Non-blocking vs blocking

### blocking 

해당하는 코드, 작업이 완료될때까지 기다려서 다른 작업을 동시에 진행하지 못한다.

### Non-blocking

Node.js는 Non-blocking을 사용한다. 그 이유는 JavaScript가 Non-blocking이기 때문인데, 그 이유는 JavaScript가 웹브라우저 상에서 작동하는 언어이기 때문이다.

만약 JS가 blocking모델이었다면, 브라우저상에서 버튼을 클릭했을때 브라우저가 멈춰버릴 것이다. 

또한 JS는 event 즉, 클릭과 같은 이벤트 주도방식의 언어인데, 쓰래드기반의 다른 언어들과는 다르게, event기반이기 때문에 비동기작업을 잘 처리할 수있다.



