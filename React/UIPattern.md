# props를 응용한 UI 제작 패턴
모달창은 보통

1. 모달창이 현재 보이는/보이지않는 상태정보를 state로 저장한다.
2. state가 true일 때 모달창 보여주라고 if문을 쓰고
3. state가 false일 때 모달창을 숨기라고 if문을 썼다.

UI만드는 패턴도 비슷하다. 제목을 눌렀을 때 해당 제목으로 바뀌는 모달창을 만든다고 가정했을 때,
1. 몇 번째 제목을 눌렀는지 상태정보를 state로 저장하고
2. state가 0일 때는 0번째 제목을 출력하고,
3. state가 1일 때는 1번째 제목을 출력하면 된다.

우선 버튼을 3개 만들어서 글을 대체해보자.
각각의 버튼을 누르면 다른 제목의 모달제목이 떠야한다.
```jsx
function App() {
  return (
    <div>
      ...
      <button onClick={ () => {} }>버튼1</button>
      <button onClick={ () => {} }>버튼2</button>
      <button onClick={ () => {} }>버튼3</button>

      <Modal />
    </div>
  )
}

function Modal(props) {
  return(
    <div className="modal">
      <h2>{props.title[방금누른번호]}</h2>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```

1. 버튼 3개를 만들고
2. 각각 버튼을 누르면 글제목이 수정되어야 하기 때문에 Modal 컴포넌트 안에 제목부분을 `props.title[방금누른글번호]` 라고 수정했다.


이제 `[방금누른글번호]`가 0이면 0번째 제목이, 1이면 1번째 제목이 뜨게하면 된다. 중요한 정보니까 App 컴포넌트 안에 state로 만드는 것이 좋다. 

```jsx
function App () {
  let [누른제목, 누른제목변경] = useState(0);
  return (
    <div>
      ...
      <button onClick={ () => {} }>버튼1</button>
      <button onClick={ () => {} }>버튼2</button>
      <button onClick={ () => {} }>버튼3</button>

      <Modal />
    </div>
  )
}

function Modal(props) {
  return(
    <div className="modal">
      <h2>{props.title[누른제목]}</h2>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```
App 컴포넌트 안에 `누른제목`이라는 state를 만들고 기본값을 0으로 주고, Modal 컴포넌트에서 `props.title[누른제목]`으로 사용했다. 하지만 이렇게 사용하면 에러가 난다. 

```jsx
function App () {
  let [누른제목, 누른제목변경] = useState(0);
  return (
    <div>
      ...
      <button onClick={ () => {} }>버튼1</button>
      <button onClick={ () => {} }>버튼2</button>
      <button onClick={ () => {} }>버튼3</button>

      <Modal title={title} 누른제목={누른제목} />
    </div>
  )
}

function Modal(props) {
  return(
    <div className="modal">
      <h2>{props.title[props.누른제목]}</h2>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```
부모가 가진 state를 쓰려면
1. `<Modal />`에서 원하는 이름의 props를 전송하고
2. 모달 안에서 props.이름 이런식으로 써야 작동한다.

이제 모달창은 `누른제목`이라는 state의 숫자의 따라 제목이 변경된다. state에 0, 1, 2 와 같은 숫자를 부여하면 각각 다른 제목이 뜰 것이다.

<br />

## 반복) 버튼을 눌렀을때 state 변경하기
0번째 버튼을 누르면 `누른제목`이라는 state가 0이,
1번째 버튼을 누르면 `누른제목`이라는 state가 1이 되어야한다.
```jsx
function App () {
  let [누른제목, 누른제목변경] = useState(0);
  return (
    <div>
      ...
      <button onClick={ () => { 누른제목변경(0) } }>버튼1</button>
      <button onClick={ () => { 누른제목변경(1) } }>버튼2</button>
      <button onClick={ () => { 누른제목변경(2) } }>버튼3</button>

      <Modal title={title} 누른제목={누른제목} />
    </div>
  )
}

function Modal(props) {
  return(
    <div className="modal">
      <h2>{props.title[props.누른제목]}</h2>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```
state 변경함수를 통해 `onClick={ () => { 누른제목변경(0) } }`로 만들었다. 이제 직접 글제목에 가서 state가 변경되게 만들어보자.

<br />

## 글제목 부분에 가서 누르면 state가 변경
```jsx
function App() {
  return(
    <div>
      ...
      { title.map((data) => {
        return (
          <div className="list">
            <h3 onClick={ () => { 누른제목변경(0) } }> {data} </h3>
          </div>
        )
      })}
    </div>
  )
}
```
지금은 `누른제목변경(0)`으로 하드코딩되어 있어서 `누른제목변경(반복문이 돌 때마다 0, 1, 2 가 되는 변수)`를 넣으면 된다. 

```jsx
function App() {
  return(
    <div>
      ...
      { title.map((data, i) => {
        return (
          <div className="list">
            <h3 onClick={ () => { 누른제목변경(i) } }> {data} </h3>
          </div>
        )
      })}
    </div>
  )
}
```
map 반복문을 쓸 때, `i`라는 파라미터를 두번째로 추가하면 반복문이 돌면서 0, 1, 2, 3... 이렇게 하나씩 증가하는 정수를 쓸 수 있다. 그걸 이용해서 `누른제목변경(i)`로 입력했다.

> map 반복문을 쓰면 콘솔창에 warning이 뜬다. 이유는 key={} 속성을 안적어서 나타난다. 리액트는 반복문을 돌린 HTML 요소엔 꼭 key={}를 적도록 권장한다. key={} 안에는 0, 1, 2, 3... 처럼 하나씩 증가하는 변수를 넣으면 되는데, 두번째 파라미터로 넣었던 i를 넣으면 된다.

<br />

### 결론
UI만드는 방법은 
1. state를 만들고
2. state가 이런 상태면 UI를 이렇게 보여주라고 코드를 짠다.
3. 그리고 버튼 누르면 state를 이렇게 바꿔주라고 코드를 짠다.


<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)