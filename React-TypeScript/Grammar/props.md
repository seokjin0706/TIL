# props

## props란?
* 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달해주는 객체이다.
* 함수도 전달이 가능하다.

## 사용법

1. props에 전달한 Object의 type을 지정
2. 하위 컴포넌트의 속성에 키-값 형식으로 데이터 전달


``` typescript
function App() {
  let [postTitle, setPostTitle] = useState('제목');

  return (
    <div className="App">
      <Modal postTitle={postTitle} setPostTitle={setPostTitle}/>
    </div>
  );
}

interface postProps{
  postTitle : string,
  setPostTitle : React.Dispatch<React.SetStateAction<string>>

}

function Modal(props : postProps){
  
  return (
    <h4>{props.postTitle}</h4>
   
  )
}


```
