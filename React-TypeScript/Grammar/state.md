# useState

## 변수 대신에 state에 데이터를 저장해서 쓰는 이유

* state는 변동사항이 생기면 state를 사용하는 html을 자동으로 재렌더링을 해준다.
* 변수는 바로 반영 x 
* 자주변경될 가능성이 있는 데이터를 useState에 저장하면 좋다.

## useState 사용법

* useState를 사용해서 데이터를 저장해 둘 수 있다.

* destructuring을 통해서 데이터 두 개를 꺼내오는데

    * 첫 번째 데이터는 state에 넣은 값으로 기본 자료형, 객체 등이 될 수 있음  
    * 두 번째 데이터는 state의 상태 값을 변경 할 수 있는 함수이다.



``` typescript
import {useState} from 'react';

function App() {
  let [like, setLike] = useState(0);
  return (
    <div className="App">
      <span onClick={()=>{setLike(like + 1)}}>👍 {like}</span>
          
    </div>
  );
}

```
 
# useState

## 변수 대신에 state에 데이터를 저장해서 쓰는 이유

* state는 변동사항이 생기면 state를 사용하는 html을 자동으로 재렌더링을 해준다.
* 변수는 바로 반영 x 
* 자주변경될 가능성이 있는 데이터를 useState에 저장하면 좋다.

## useState 사용법

* useState를 사용해서 데이터를 저장해 둘 수 있다.

* destructuring을 통해서 데이터 두 개를 꺼내오는데

    * 첫 번째 데이터는 state에 넣은 값으로 기본 자료형, 객체 등이 될 수 있음  
    * 두 번째 데이터는 state의 상태 값을 변경 할 수 있는 함수이다.



``` typescript
import {useState} from 'react';

function App() {
  let [like, setLike] = useState(0);
  return (
    <div className="App">
      <span onClick={()=>{setLike(like + 1)}}>👍 {like}</span>
          
    </div>
  );
}
```

## useState Array, Object 상태 값 변경 (상태의 불변성)

* useState에서 상태 값을 변경하는 함수의 인자에 원본 상태 값과 다른 상태 값을 전달할 때 재렌더링을 해준다.

* Array, Object를 copy없이 그대로 전달하면 원본 상태 값과 같은 주소를 가리키므로 false가 돼서 재렌더링이 일어나지 않는다.

* 즉 Array, Object에 대한 copy를 하고 copy한 Array, Obejct를 수정해서 인자로 넘겨야한다.

``` typescript
function App() {
 
  let [arr, setArr] = useState(['data1', 'data2']);

  
  return (
    <div className="App">
      <h1>{arr[0]}</h1>
      <h1>{arr[1]}</h1>
      <button onClick={()=>{
        let copyArr = [...arr];
        copyArr[0] = 'changed';
        setArr(copyArr);
      }}>1번 데이터 수정</button>
    </div>
  );
}
```


 


