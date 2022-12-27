# 컴포넌트 Lifecycle

* 컴포넌트는 생성 된다(mount)
* 컴포넌트는 재렌더링이 된다. (update)
* 컴포넌트는 삭제가 된다. (unmount)

mount, update, unmount 각각에 대해서 특정 코드를 실행할 수 있음


[class를 이용한 예전 문법]
``` typescript
class Detail extends React.Component {
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

useEffect(()=>{
//mount, update 마다 실행되는 코드
});

```

* useEffect 안에 적은 코드는 html 렌더링 완료 후에 동작한다.
* 오래 걸리는 코드를 useEffect 안에 작성하면 html이 다 보이고 난 후에 연산을 시작
* 오래걸리는 반복 연산, 서버에서 데이터 가져오기, 타이머 등..

``` typescript
useEffect(()=>{
for(let i=0; i < 100000000; i++){

}
});
```

# useEffect에 실행 조건을 넣을 수 있다
* [] 안에 있는 state가 변할 때만 useEffect 안의 코드가 실행 된다.
* 아무것도 넣지 않으면 컴포넌트 mount할 때(로드할 때) 한 번만 실행한다.
* [] 안에 여러 state를 넣을 수 있음
``` typescript
useEffect(()=>{

}, [state]);
```

# clean up function
* useEffect가 동작하기 전에 특정 코드를 실행하고 싶을 때 사용한다.
* `return () => {실행할 코드}`
* 타이머제거, socket 연결 요청제거, ajax 요청 중단 코드에서 많이 작성
* 컴포넌트 unmount 시에도 clean up function 1회 실행

``` typescript
  useEffect(()=>{
    나중에 실행되는 코드

    return () =>{
        먼저 실행되는 코드
    }
  }, [state]);
```

[ex]
``` typescript
let [visibleBox, setVisibleBox] = useState(true);
    let [boxTime, setBoxTime] = useState(2);
    useEffect(()=>{
        let timer =setTimeout(()=>{
          console.log(boxTime);
          if(boxTime > 0) setBoxTime(boxTime -1);
          else setVisibleBox(false);
        }, 1000)
        return () =>{
          clearTimeout(timer);
        }
    }, [boxTime])
```
