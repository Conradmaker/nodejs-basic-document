# process

현재 실행중인 노드 프로세스에 대한 정보를 담고 있음.

* 컴퓨터마다 출력값이 다를 수 있다. 

ex\)

```text
process.arch  
    x64 //프로세서 아키텍쳐 정보
process.platform
    win32 //운영체제 플랫폼 정보
process.pid
    15928 //현재 프로세스의 아이디
process.uptime()
    199.35 //프로세스가 시작된 후 흐른 시간
process.cwd()
//현재 프로세스가 실행되는 위치
```



### process.env

시스템 환경변수들이 들어있는 객체 

* 비밀키를 보관하는 요도로도 쓰인다 . 
* 환경변수는 process.env로 접근 가능 

일부 환경변수는 노느 실행시 영향을 미친다. 

process.nextTick\(콜백\)

Promise와 process.nextTick은 새치기를 한다.



process.exit\(0\)

서버가 종료된다.  0이 아니라 1이 들어가면 에러가 있음을 나타낸다. 



