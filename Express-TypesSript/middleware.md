# 미들웨어

- HTTP 요청과 응답 사이에 단계별 동작을 수행해주는 함수
- 미들웨어는 HTTP 요청이 들어온 순간부터 순차적으로 실행
- HTTP 요청과 응답 객체를 처리하거나, next함수 호출로 다음 미들웨어를 실행할 수 있다.

# example

```typescript
import * as express from "express";

const app = express();
const port = 8000;

app.use((req, res, next) => {
  console.log(req.rawHeaders[1]);
  console.log("this is logging middleware");
  next();
});

app.get("/cats/som", (req, res, next) => {
  console.log("this is som middleware");
  next();
});

app.get("/", (req: express.Request, res: express.Response) => {
  res.send({ cats: Cat });
});
app.get("/cats/blue", (req: express.Request, res: express.Response) => {
  res.send({ blue: Cat[0] });
});

app.get("/cats/som", (req: express.Request, res: express.Response) => {
  res.send({ som: Cat[1] });
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```
