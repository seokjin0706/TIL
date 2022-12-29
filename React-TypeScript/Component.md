# Component

* 긴 HTML을 한 단어로 치환할 수 있는 문법
* Component명은 영어 대문자로 시작
* return() 안엔 태그 하나만을 사용해서 나머지 태그들을 감싸야한다.
* App도 Component이므로 App 밖에 선언, Component 안에 Component를 만들지 않는다.

# 어떤 HTML을 Component로 만들까?

* 사이트에서 반복해서 나오는 HTML 덩어리들
* 내용이 자주 변할 거 같은 HTML 부분
* 다른 페이지를 만들 때 그 페이지의 HTML을 하나의 Component로 만든다.
* 함수의 용도랑 비슷하다고 생각하면 된다.

``` typescript

function App (){
  return (
    <div>
      <Modal></Modal>
    </div>
  )
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

