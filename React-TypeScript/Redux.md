# Redux
* Redux는 props없이 state를 공유할 수 있게 도와주는 라이브러리

* ts 파일 하나에 state들을 보관할 수 있고 모든 컴포넌트에서 직접 꺼내쓸 수 있다.

* 컴포넌트간 state 공유가 편하다.


## Redux toolkit 설치

`npm install @reduxjs/toolkit react-redux`

## 세팅
1. store.ts 파일 생성

2. store.ts 파일 작성

[store.ts]
``` typesscript
import {configureStore} from '@reduxjs/toolkit';

export default configureStore({
    reducer : {
        
    }
})

```
3. index.tsx 파일에서 store import 및 Provider 컴포넌트로 App 감싸기

[index.tsx]
``` typescript
import { Provider } from 'react-redux';
import store from './store';
const root = ReactDOM.createRoot(
  document.getElementById('root') as HTMLElement
);
root.render(
  <React.StrictMode>
    <Provider store={store}>
      <BrowserRouter>
       <App />
      </BrowserRouter>
    </Provider>
    
  </React.StrictMode>
);
```

## Redux Store에 state 보관하기

1. store.ts 피일에서 createSlice()로 state 만들고
2. configureStore() 안에 state 등록

[store.ts]
``` typescript
import {createSlice ,configureStore} from '@reduxjs/toolkit';
let user = createSlice({
    name : 'user',
    initialState : 'kim',
    reducers: {}
})
export default configureStore({
    reducer : {
        user : user.reducer,
    }
})
```

## Redux Store에 보관한 state 가져다 쓰기

``` typescript
import { useSelector } from 'react-redux/es/exports';
interface StateType{
    user : string
}
function Com(){
    let s = useSelector((state : StateType)=>{return state})
    console.log(s);
    return(
    );
}

export {Com};
```

## Redux state를 변경하는 방법
* store.ts 파일에서 state 변경해주는 함수 만들고 export
* 사용할 때 import해서 dispatch()로 감싸서 호출

1. store.ts 파일에서 state 변경 함수 만들고 export

* `createSlice()` 함수 안에서 `reducers` 안에 변경 함수 만들고 export
* 변경 함수에 파라미터를 전달하면 기존 state와 동일
* `{stateName}.actions`하면 모든 함수를 다 가져올 수 있다.

[store.ts]
``` typescript
let user = createSlice({
    name : 'user',
    initialState : 'kim',
    reducers: {
        setName(state){
            return 'john' + state;
        }
    }
})

export let {setName} = user.actions
```

2. 필요한 곳에서 state 변경 함수 사용하기

`useDispatch`, `변경 함수` import 후 `dispatch`로 `변경 함수` 감싸서 호출

[use.ts]
``` typescript
import { useSelector } from 'react-redux/es/exports';
import { useDispatch } from 'react-redux/es/hooks/useDispatch';
import {setName} from './../store';

let dispatch = useDispatch();
dispatch(setName());
```

## Redux 변경 함수에서 Object/Array 자료형은 복사본을 만들 필요 없이 바로 수정해도 변경이 잘 된다.

```typescript
let cart = createSlice({
    name : 'cart',
    initialState : [
        {id : 0, name : 'White and Black', count : 2},
        {id : 2, name : 'Grey Yordan', count : 1}
      ],
    reducers: {
        increaseCount(state, action : PayloadAction<number>){
            state[0].count+=action.payload;
        }
    }
})
```

## Redux state 변경 함수에서 파라미터 사용하기
변경 함수에 파라미터 넣고 `파라미터.payload`로 사용 가능
``` typescript
let user = createSlice({
    name : 'user',
    initialState : 'kim',
    reducers: {
        setName(state, action : PayloadAction<string>){
            return 'john' + state + action.payload;
        }
    }
})

// 다른 파일..
dispatch(setName('add'));
```
