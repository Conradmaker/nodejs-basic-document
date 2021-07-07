# Bridge Pattern

동일한 UI에 대해 여러가지 패턴을 제공할때 브릿지 패턴을 사용할 수 있다 .

 ex\) 다크모드

```javascript
/*
Webpage interface :

constructor(theme)
getContent()
*/

class About {
  constructor(theme) {
    this.theme = theme;
  }

  getContent() {
    return "About page in " + this.theme.getColor();
  }
}

class Careers {
  constructor(theme) {
    this.theme = theme;
  }

  getContent() {
    return "Careers page in " + this.theme.getColor();
  }
}

/*
Theme interface :

getColor()
*/

class DarkTheme {
  getColor() {
    return "Dark Black";
  }
}
class LightTheme {
  getColor() {
    return "Off white";
  }
}
class AquaTheme {
  getColor() {
    return "Light blue";
  }
}

//전달
const darkTheme = new DarkTheme();

const about = new About(darkTheme);
const careers = new Careers(darkTheme);

console.log(about.getContent()); // "About page in Dark Black"
console.log(careers.getContent()); // "Careers page in Dark Black"

```

