# export와 export default의 차이

## export default
* 해당 모듈엔 하나의 개체(변수, 클래스, 함수 등)만 있다는 의미로 받아들여진다.
* 원하는 이름으로 import 가능

[data.ts]
``` typescript
let data = 10;
export default data;
```
[App.tsx]
``` typescript
import myData from "./data";
```

# export
* 복수의 개체가 있는 라이브러리 형태의 모듈에서 가져올 때 사용한다.
* 특쟁 개체만 가져올 수 있따.
* 원하는 이름으로 import가 불가능하다.

[data.ts]

``` typescript
let data = 10;
export {data};
```
[App.tsx]
``` typescript
import {data} from "./data";
```
