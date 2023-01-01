# localStorage
* state 데이터를 브라우저에 임시로 저장하는 방법
* 약 5MB 문자 데이터 저장 가능
* key/value 형태로 저장
* 유저가 브라우저를 청소하지 않는 이상 영구적으로 남아있다.

## 사용법

```typescript
localStorage.setItem('key', 'value');
localStorage.getItem('key');
localStorage.removeItem('key')
```

## Array/Object 자료 set, get 방법
``` typescript

localStorage.setItem('obj', JSON.stringify({name:'kim'}) );
let data = localStorage.getItem('obj');
var p = JSON.parse(data)
```
