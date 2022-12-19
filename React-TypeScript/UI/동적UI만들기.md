# 리액트에서 동적인 UI 만드는 단계

1. html, css로 미리 UI 디자인을 만든다.
2. UI의 현재 상태를 state로 저장하고
3. state에 따라서 UI가 어떻게 보일지 조건문(JSX 삼항연산자...) 등으로 작성한다.

``` typescript

function App() {
  let [modal, setModal] = useState(false);
  
  return (
    <div className="App">
      <button onClick={()=>{setModal(!modal);}}>On/Off</button>
      
      {
        modal === true ? <Modal/> : null
      }
    </div>
  );
}
function Modal(){
  return (
    <div className="modal">
      <h4>제목</h4>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}

```
