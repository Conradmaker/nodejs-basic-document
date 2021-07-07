# Router분리

Router가 너무 많아지게 되면 app.js가 너무 길어지기 때문에 app.js가 길어지는 것을 막을 수 있다. 

app.js에서는 다음과 같이 작성해준뒤 

```javascript
const indexRouter  = require('./routes');
const userRouter  = require('./routes/user');

app.use('/',indexRouter);
app.use('/user',userRouter);
```

다음 routes폴더를 만들고 그 안에 index.js

```javascript
const express = require('express');

const router = express.Router();

//GET/라우터
router.get('/',(req,res)=>{
    res.send('hello, Express');
})

module.exports = router
```

이렇게 되면 app에서의 경로와 router의 경로가 합쳐져서 나온다. 



## Router그룹화

주소는 같지만 메서드가 다른 코드가 있을때

ex

```javascript
router.get("/abc", (req, res) => {
  res.send("GET/abc");
});
router.post('/abc',(req,res)=>{
  res.send('POST/abc')
})
```

를 다음과 같이 그룹화할 수 있다. 

```javascript
router.route("/abc")
  .get((req, res) => {
    res.send("GET/abc");
  })
  .post((req, res) => {
    res.send("POST/abc");
  });
```

