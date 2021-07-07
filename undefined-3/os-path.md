# os / path

node에서 미리 모듈로 만들어 놓은 것들은 바로 불러올 수 있다. 

## os

![](../.gitbook/assets/image%20%2835%29.png)

os.cpus\(\) 는 코어의 갯수를 알아보는데 자주 사용되니 알아두자. 

![](../.gitbook/assets/image%20%2811%29.png)

## path

경로처리할때 중요한 부분이다. 

윈도우에서는 아래와 같은 방법을 사용한다. 

```text
C:\users\conrad
```

맥에서는 다음과 같은 방법을 사용한다. 

```text
/user/conrad
```

이런 다르게 표기되는 경로를 path처리 해주면 같게 변환된다. 

ex\)

```text
path.join(__dirname,'var.js');
```

![](../.gitbook/assets/image%20%283%29.png)

