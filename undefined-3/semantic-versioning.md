# Semantic Versioning

npm에 보다보면 패키지들의 버전이 X.X.X으로 관리되고 있는것을 볼 수 있다.

Semantic Versioning은 일반적인 오픈소스에서 체계적이고, 의미있는 버전체계를 가지게 하기 위해 효율적으로 버전을 관리하는 방법이다.

보통 X.X.X 3자리로 표현하게 되는데, 각각 의미를 가지고 있다.



​X.X.X

첫번째자리 : 하위호환이 유지되지 않을 정도로 새로운 기능이 추가되었을 때

두번째자리 : 하위호환이 되는 새로운 기능

새번째자리 : 보통 버그픽스



patch releases : 1.0   /   1.0.x   /   ~1.0.4

minor releases : 1 / 1.x / ^1.0.4

major releases : \*  /  x

