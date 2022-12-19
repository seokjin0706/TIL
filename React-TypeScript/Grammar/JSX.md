# react는 html 대신에 JSX를 사용한다.
 
## jsx란?

1. JSX(JavaScript XML)는 JavaScript에 XML을 추가해 확장한 문법이다.

2. 브라우저에서 실행하기 전에 자바스크립트 형태의 코드로 변환된다.

3. TypeScript는 .tsx 파일을 만들어야 함

## 반드시 부모 요소 하나가 감싸는 형태여야 한다.

Virtual DOM에서 컴포넌트 변화를 감지할 때 효율적으로 비교할 수 있도록 컴포넌트 내부의 하나는 DOM 트리 구조로 이루어져야 한다는 규칙이 있다.

``` typescript
function App() {
    return (
        <div className="App">
            <div>value</div>
        </div>
    );
}

```

## className

html에 class 넣을 때 className 사용
      
``` html
<div className="App"></div>
```

## 데이터 바인딩

변수를 html에 삽입할 때는 {변수} 중괄호를 사용한다.  

``` typescript
function App() {
    let data = 'value';
    return (
        <div className="App">
            <div>{data}</div>
        </div>
    );
}
 ```

## html에 style 속성 넣기
{}중괄호 안에 object를 넣어야한다.

``` html
<div style={{color:'blue', fontSize:'30px'}}>value</div>      
```

## 삼항 연산자

* JSX HTML 내부에서 if문을 사용할 수 없다  
* 조건부로 HTML을 보여주고 싶을 때는 삼항 연산자를 사용할 수 있다.

``` typescript

function App() {
  let [modal, setModal] = useState(false);
  return (
    <div className="App">
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

## map을 이용한 반복문

* JSX 안에서 for을 사용할 수 없어서 HTML을 반복하고 싶으면 map을 사용
* map에서 return할 때마다 그 값은 배열에 하나씩 저장되고 map 함수가 끝나면 해당 배열을 리턴하는데 JSX는 중괄호 안에 배열이 있으면 배열의 원소를 하나씩 꺼내서 HTML로 출력해준다.
* map 반복문으로 생성한 html에 key={key} 속성을 추가해야한다. (React가 태그를 구분할 수 있게 하기 위함)




``` typescript

function App(){
  let arr = ['data1', 'data2', 'data3'];
  return (
    <div className='App'>
      {
        arr.map((value, index)=>{
          return (
            <div key={index}>{value}</div>
          );
        })
      }
    </div>
   
  );
}

```
