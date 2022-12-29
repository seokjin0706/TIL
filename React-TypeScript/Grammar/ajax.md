# AJAX?
서버에 GET, POST 요청을 할 때 새로고침 없이 데이터를 주고받을 수 있게 도와주는 브라우저 기능

# axios 
AJAX를 위한 외부 라이브러리
## 설치
`npm i axios`

## import
`import axios from 'axios';`

## get 요청

``` typescript
axios.get('url')
.then((result)=>{
    console.log(result);
    console.log(result.data);
})
.catch(()=>{
    console.log('요청 실패');
})

```

## post 요청

``` typescript

axios.post('url', {key : 'value'})
.then()
.catch()

```

## 동시에 여러 개의 AJAX 요청 보내기

``` typescript

Promise.all( [axios.get('URL1'), axios.get('URL2')] )\
.then()
.catch()
```
