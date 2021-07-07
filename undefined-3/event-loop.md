# event loop

loupe 사이트에 가면 직관적으로 코드가 어떤 순서로 진행되는지 확인할 수 있다.

직접 작성한 코드를 들고 가져가보자!

{% embed url="http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D" %}

좀 이상하지만 위 사이드 맞다...

선언되면 메모리\(heap\)에 쌓이게 된다. 

호출되면 호출스택에 쌓이고 역할이 끝나면 빠진다 . 

만약 setTimeout같은 비동기코드가 실행되면, 호출스택뿐만 아니라 백그라운드에도 저장되서 기능을 수행한다 . 

setTimeout이 끝나면 백그라운드에 있던게 태스크 큐로 옮겨지게 되고, 태스크큐는 호출스택으로 쌓아준다 . 

결국 호출스택, 백그라운드, 태스크큐가 모두 비어지게 되면, 코드가 끝나는 것이다. 

참고로 백그라운드로 갈수있는것은 정해져 있으니 외워두면 좋다. 

