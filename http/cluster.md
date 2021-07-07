# Cluster

http2를 적용하면서 Cluster도 함께 적용하면 좋다. 

### 기본적으로 싱글 스레드인 노드가 CPU 코어를 모두 사용할 수 있게 해주는 모듈

* 포트를 공유하는 노드 프로세스를 여러개 둘 수 있음
* 요청이 많이 들어왔을 때 병렬로 실행된 서버의 개수만큼 요청이 분산됨
* 서버에 무리가 덜감
* 코어가 8개인 서버가 있을때 : 보통은 코어 하나만 활용
* cluster로 코어 하나당 노드 프로세스 하나를 배정 가능
* 성능이 8배가 되는것은 아니지만 개선됨
* 단점: 컴퓨터 자원\(메모리, 세션등\) 공유하지 못함
* Redis등 별도 서버로 해결

## 서버 클러스터링

### 마스터 프로세스와 워커 프로세스

* 마스터 프로세스는 CPU 개수만큼 워커 프로세스를 만든다.\(worker\_threads랑 구조 비슷\)
* 요청이 들어오면 워커 프로세스에 고르게 분배

```javascript
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length; //cpu갯수만큼

if (cluster.isMaster) { //마스터 프로세스
  console.log(`마스터 프로세스 아이디: ${process.pid}`);
  // CPU 개수만큼 워커를 생산
  for (let i = 0; i < numCPUs; i += 1) {
    cluster.fork();
  }
  // 워커가 종료되었을 때
  cluster.on('exit', (worker, code, signal) => {
    console.log(`${worker.process.pid}번 워커가 종료되었습니다.`);
    console.log('code', code, 'signal', signal);
    cluster.fork(); //하나 종료되었을때 하나 다시 만들어준다. 
  });
} else {
  // 워커들이 포트에서 대기
  http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
    res.write('<h1>Hello Node!</h1>');
    res.end('<p>Hello Cluster!</p>');
    setTimeout(() => { // 워커 존재를 확인하기 위해 1초마다 강제 종료
      process.exit(1);
    }, 1000);
  }).listen(8086);

  console.log(`${process.pid}번 워커 실행`);
}
```

![&#xD504;&#xB85C;&#xC138;&#xC2A4;&#xB294; &#xCD1D; 9&#xAC1C;&#xC9C0;&#xB9CC; &#xC11C;&#xBC84;&#xB294; 8&#xAC1C; &#xC2E4;&#xD589;](../.gitbook/assets/image%20%2832%29.png)

서버로 들어가 새로고침을 한번 할때마다 서버가 하나씩 꺼질 것이다. 

하지만 워커 종료시에 하나를 다시 만들어주기 때문에 꺼지지 않을것이다.



서비스를 할때는 http2, cluster등을 이용해 여러가지 서버 안전장치를 구현해 놓는것이 중요하다.

지금까지 서버를 만드는 것을 배워보았는데, 사실 코드가 많이 지저분하다. 

그렇다면 이제는 Framework를 사용해 서버를 좀더 간단하고 가독성 좋게 만들어보자. 



