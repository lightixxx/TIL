# component
복잡한 HTML을 한 단어로 깔끔하게 치환할 수 있는 문법이다.

예를 들어 모달창을 만든다고 가정해보자.
```jsx
function App() {
  return (
    <div>
      <p>복잡한 HTML</p>
      ...
      <Modal />
      <Modal></Modal>
    </div>
  )
}

function Modal() {
  return (
    <div className="modal">
      <h2>제목</h2>
      <p>내용</p>
    </div>
  )
}
```
이렇게 `Modal`이라는 함수 안에 `return()`에 원하는 HTML을 담은 뒤 `<Modal />`로 HTML을 한 단어로 줄일 수 있다.

이렇게 축약한 HTML 덩어리들을 Component라고 부른다. 나중에 유지보수하기 편해진다.

<br />

## Component의 특징
- 대문자로 시작한다.
- `return()`안에는 태그들이 평행하게 들어갈 수 없다. `<div>`나 `<>`(fragments)로 묶어주어야 한다.
- component 안에 미리 만들어둔 component를 넣을 수도 있다.

<br />

## Component로 만들면 좋은 HTML
- 사이트에 반복해서 사용하는 HTML
- 내용이 자주 변경될 것 같은 HTML 부분
- 다른 페이지를 만들고 싶을 때 그 페이지의 HTML 내용을 하나의 컴포넌트로 만드는 것이 좋다
- 다른 팀원과 협업할 때 웹페이지를 컴포넌트 단위로 나눠서 작업을 분배

<br />

## Component의 단점
컴포넌트가 `App(){}` 안에 있는 state를 사용하고 싶을 떄 바로 사용할 수 없다. [props](https://github.com/lightixxx/TIL/blob/master/React/props.md)라는 문법을 이용해 state를 해당 컴포넌트에까지 전해줘야 사용이 가능하다.

<br />
<br />
<br />

##### 출처
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)