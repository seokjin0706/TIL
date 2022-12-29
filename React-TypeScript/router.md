# 라우팅하기

## 패키지 설치
`npm install react-router-dom @types/react-router-dom`

## index.tsx 파일에서 BrowerRouter로 App 감싸기
[index.tsx]
``` typescript
<BrowserRouter>
    <App />
</BrowserRouter>
```
## App.tsx에서 Router, Route, Link를 사용하여 라우팅
[App.tsx]

``` typescript
import { Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <div className="App">
      <Link to="/">Home</Link>
      <Routes>
        <Route path="/" element={<Main />} />
      </Routes>
    </div>
  );
}

```

## useNavigate() : 페이지 이동

*  `navigate('/')` : '/'로 이동
* `navigate(1)` : 앞으로 가기
* `navigate(-1)` : 뒤로 가기


``` typescript
import {useNavigate } from 'react-router-dom';
function App() {
  let navigate  = useNavigate();
  return (
    <div className="App">
      <button onClick={()=>{ navigate('/') }}>Home</button>
    </div>
  );
}
```

## 404 페이지 만들기

path="*"은 모든 경로를 의미, 따라서 위에 일치하는 경로가 없을 경우 실행

``` typescript
<Route path="*" element={ <div>404페이지</div> } />
```

## nested routes
상위 컴포넌트를 재사용해서 서브 경로를 만들 수 있음
```
/about/member
/about/location
```
위와 같은 경로가 있을 때 /about의 서브 경로가 있을 때 /about의 내용을 재사용해서 일부분만 수정해서 서브 경로의 페이지를 보여주고 싶을 때 사용한다. 

* `<Route> 안에 <Route>`를 넣는다.

* 상위 컴포넌트에서 `<Outlet>`을 사용해서 서브 컴포넌트를 어디에 보여줄지 지정해야됨.

``` typescript
import { Routes, Route, Outlet } from 'react-router-dom'

<Route path="/about" element={ <About/> } >  
  <Route path="member" element={ <div>멤버</div> } />
  <Route path="location" element={ <div>위치</div> } />
</Route>

function About(){
  return (
    <div>
      <h4>about페이지</h4>
      <Outlet></Outlet>
    </div>
  )
}

```

## URL 파라미터 사용하기 (useParams)
``` typescript
<Route path="/detail/:id" element={ <Detail shoes={shoes}/> }/>

import { useParams } from 'react-router-dom';

let {id} = useParams();
```
