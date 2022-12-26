# 컴포넌트 Lifecycle

* 컴포넌트는 생성 된다(mount)
* 컴포넌트는 재렌더링이 된다. (update)
* 컴포넌트는 삭제가 된다. (unmount)

mount, update, unmount 각각에 대해서 특정 코드를 실행할 수 있음


[class를 이용한 예전 문법]
``` typescript
class Detail2 extends React.Component {
  componentDidMount(){
    //Detail2 컴포넌트가 로드되고나서 실행할 코드
  }
  componentDidUpdate(){
    //Detail2 컴포넌트가 업데이트 되고나서 실행할 코드
  }
  componentWillUnmount(){
    //Detail2 컴포넌트가 삭제되기전에 실행할 코드
  }
}
```


# useEffect
[최근에 사용하는 방식]
``` typescript
import {useState, useEffect} from 'react';

function Detail(){

  useEffect(()=>{
    //mount, update 마다 실행되는 코드
  });
  
  return (

  );
}

```

* useEffect 안에 적은 코드는 html 렌더링 완료 후에 동작한다.
* 오래 걸리는 코드를 useEffect 안에 작성하면 html이 다 보이고 난 후에 연산을 시작
* 오래걸리는 반복 연산, 서버에서 데이터 가져오기, 타이머 등..

``` typescript
function Detail(){

  useEffect(()=>{
    for(let i=0; i < 100000000; i++){

    }
  });
  
  return ()
  ;
}
```
