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
