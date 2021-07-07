# Adapter Pattern

Class의 interface를 사용자가 기대하는 다른 interface로 변환하는 패턴 

호환성이 없는 interface때문에 함께 작동할 수 없는 다른 클래스들이 함께 작동할 수 있도록 해준다 .

```javascript
*/

//roar라는 동작을 가지고 있는 사자
/*
Lion interface :

roar()
*/

class AfricanLion {
  roar() {}
}

class AsianLion {
  roar() {}
}

//roar라는 매소드가 정의되있기 때문에 사용가능
class Hunter {
  hunt(lion) {
    // ... some code before
    lion.roar();
    //... some code after
  }
}

//Asian Lion과는 다르게 loar가 아닌 bark가 있다.
// This needs to be added to the game
class WildDog {
  bark() {}
}

// Adapter around wild dog to make it compatible with our game
class WildDogAdapter {
  constructor(dog) {
    this.dog = dog;
  }

  roar() {
    this.dog.bark();
  }
}
```

