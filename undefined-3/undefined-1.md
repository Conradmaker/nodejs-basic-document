# 호출스택

호출스택 \( 함수의 호출, 자료구조의 스택

* Anomymoius는 가상의 전역 커텍스트 \( 항상 있다고 생각\)
* 함수 호출 순서대로 쌓이고, 역순으로 실행됨 
* 함수의 실행이 완료되면 스택에서 빠짐 
* LIFO구조라서 스택이라고 불린다. 

```text
function first(){
    second();
    console.log('1');
}
function second(){
    third();
    console.log('2');
}
function third(){
    console.log('3');
}
first();

// 3->2->1
```

![](../.gitbook/assets/image%20%2819%29.png)

함수가 실행되는 중간에 다른 함수가 실행되면 그 위에 함수가 쌓인다 . 

{% hint style="info" %}
항상 JS코드는 위에서 아래로, 왼쪽에서 오른쪽으로 실행된다. 
{% endhint %}

### 비동기코드

```text
function run(){
    console.log('3초후 실행');
}
console.log('시작');
setTimeout(run,3000(;
console.log('끝');
```

이런 경우에는 run이 실행이 안된다 . stack에서 run이 빠져버렸기 때문에.. 

비동기를 이해하기 위해서는 event loop를 알아야 한다. 

