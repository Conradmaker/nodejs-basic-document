# npm

## npm 이란?

### Node Package Manager

* 노드의 패키지 매니저
* 다른 사람들이 만든 소스 코드들을 모아둔 저장소
* 남의 코드를 사용해 프로그래밍 가능
* 이미 있는 기능을 다시 구현할 필요가 없어 효율적
* 오픈 소스 생태계를 구성중



* 패키지: npm에 업로드된 노드 모듈
* 모듈이 다른 모듈을 사용할 수 있듯 패키지도 다른 패키지를 사용할 수 있음
* 의존관계라고 부름

## pakage.json

* 현재 프로젝트에 대한 정보와 사용중인 패키지에 대한 정보를 담은 파일
* 같은 패키지라도 버전별로 기능이 다를 수 있으므로 버전을 기록해주어야 함
* 동일한 버전을 설치하지 않으면 문제가 생길 수 있음
* 노드 프로젝트 시작 전 pakage.json부터 만들고 시작한다.\(npm init\)

```text
{
  "name": "node.5",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "conrad",
  "license": "ISC"
}
```

여기서 script부분은 사용자가 터미널에서 사용할 수 있는 명령어다.

```text
npm run test 이런식으로 실행할 수 있다.
```

### 패키지 설치

express를 설치한다고 하면

```text
npm i express
```

그러면 pakage.json에 dependencies가 생긴다.

```text
{
  "name": "node.5",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

이곳에서 설치되어 있는 패키지의 버전을 확인하고, 후에 클론했을 때,

npm install을 통해 설치할 수 있다. 

-d 를 붙여주면, 개발모드에서만 사용할 패키지를 설치할 수도 있다.

### npm 명령어

{% embed url="https://docs.npmjs.com/cli-documentation/cli" %}

이곳에서 확인!



### npm배포

npm init을 한뒤에 index.js를 만들어주세요

```text
module.exports = () => {
  return "hello pakage";
};
```

```text
{
  "name": "npmtest-7149",
  "version": "1.0.0",
  "description": "hello!",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

아 npm에 회원가입이 되있어야 합니다.

회원가입이 되어있다면, 

먼저 npm adduser를 통해 로그인을 합니다.

![](../.gitbook/assets/image%20%2828%29.png)

그뒤 pakage.json파일이 있는 폴더에서 npm publish를 실행해주세요

![&#xC131;&#xACF5;&#xC785;&#xB2C8;&#xB2E4;.](../.gitbook/assets/image%20%2822%29.png)

연습용이니 지워줘야만 합니다.. 

72시간 안에 삭제하지 않으면 영원히 남게되요..

일단 npm info를 통해 확인을 한번 해본뒤

![](../.gitbook/assets/image%20%2833%29.png)

npm unpublish 패키지명 --force 를 통해 지워주세요

![](../.gitbook/assets/image%20%2831%29.png)

