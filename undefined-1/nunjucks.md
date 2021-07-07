# Nunjucks

app.js 셋팅

```text
const express = require("express");
const nunjucks = require("nunjucks");
const app = express();

//템플릿 경로 지정 views폴더로
nunjucks.configure("views", { 
  express: app,
  watch: true,
  escape:true,
});
```

변수

![](../.gitbook/assets/image%20%2817%29.png)

반복문

![](../.gitbook/assets/image%20%2813%29.png)

조건문

![](../.gitbook/assets/image%20%2816%29.png)

include

![](../.gitbook/assets/image%20%2834%29.png)

layout

![](../.gitbook/assets/image%20%2825%29.png)



