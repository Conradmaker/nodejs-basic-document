# Decorator Pattern

주어진 상황및 용도에 따라 객체에 책임을 덧붙이는 패턴



```javascript
/*
Coffee interface:
getCost()
getDescription()
*/

class SimpleCoffee {
  getCost() {
    return 10; //가격리턴
  }

  getDescription() {
    return "Simple coffee"; //설명리턴
  }
}

```



