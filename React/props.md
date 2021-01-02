# props
props 는 properties 의 줄임말로, 어떤 값을 컴포넌트에게 전달할 때 props를 사용한다. 자식 컴포넌트에서  부모 컴포넌트의 state를 가져다쓰고 싶을 땐 props라는 문법으로 state를 전송해야한다.

<br />

## props의 기본 사용법
App 컴포넌트에서 Hello 컴포넌트를 사용할 때 `name`이라는 값을 전달해주고 싶다고 가정해보자. 여기서 App 컴포넌트는 부모 컴포넌트이고, Hello는 자식 컴포넌트이다. props 문법으로 state를 전송한 뒤 `{props.state이름}`을 쓰면 된다.

1. <자식 컴포넌트 전송할이름={state명}>
2. 자식 컴포넌트 선언하는 function 안에 파라미터 만들기.
3. props.전송할이름을 쓰면 props 사용가능.
```jsx
function App() {
  let [title, setTitle] = useState(['W.I.P', 'LOVE', 'STUDY']);

  return (
    <>
      ...
      <Modal title={title} />
    </>
  );
}

function Modal(props) {
  return <div>안녕하세요! {props.title[0]}</div>
}
```
Modal 컴포넌트에서 title 값을 사용할 땐, props는 객체형태로 전달되며, `title`의 값을 조회하고 싶다면 `props.title`을 조회하면 된다.

- props는 `<Modal title={title} desc={desc} />` 등 무한히 많이 전송할 수 있다.
- props라는 파라미터엔 전송한 모든 props 데이터가 들어가 있기때문에 `props.title` 이런식으로 원하는 것만 꺼내쓰면 된다.
- props 전송할 때 변수명을 넣고 싶다면 `<Modal title={변수명} />`중괄호를 일반 텍스트를 넣고싶으면 `<Modal title="STUDY" />` 따옴표를 넣어도 된다.


<br />

## 여러개의 props, 비구조화 할당
props 내부의 값을 조회할 때 마다 `props.`을 입력하지 않고, 함수의 파라미터에서 비구조화 할당(구조분해) 문법을 사용해서 여러 개의 props를 간결한 코드로 작성할 수 있다. 
```jsx
function Modal({color, name}) {
  return <div style={{color}}> 안녕하세요 {name} </div>
}
```

<br />

## defaultProps로 기본 값 설정
컴포넌트에 props를 지정하지 않았을 때, 기본적으로 사용할 값을 설정하고 싶을 땐 컴포넌트에 `defaultProps` 값을 설정하면 된다.

```jsx
import React from 'react';

function Hello({ color, name }) {
  return <div style={{ color }}>안녕하세요 {name}</div>
}

Hello.defaultProps = {
  name: 'no-name'
}

export default Hello;
```
App.js에서 name이 없는 Hello 컴포넌트를 렌더링하면 no-name이 렌더링 되는 것을 확인할 수 있다.

<br />

## props.children
컴포넌트 태그 사이에 넣은 값을 조회하고 싶다면 `props.children`을 조회하면 된다.

Wrapper.js 를 만든다고 가정해보자.
```jsx
import React from 'react';

function Wrapper() {
  const style = {
    border: '2px solid black',
    padding: '16px',
  };
  return (
    <div style={style}>

    </div>
  )
}

export default Wrapper;
```
Wrapper.js를 App에서 사용하면
```jsx
import React from 'react';
import Hello from './Hello';
import Wrapper from './Wrapper';

function App() {
  return (
    <Wrapper>
      <Hello />
    </Wrapper>
  );
}

export default App;
```
위 코드처럼 Hello 컴포넌트를 Wrapper 태그 내부에 넣었지만, 확인해보면 Hello 컴포넌트는 렌더링되지 않는다. 내부의 내용이 보여지게 하기 위해서는 Wrapper에서 `props.chilren`을 렌더링 해주어야한다.

```jsx
import React from 'react';

function Wrapper({ children }) {
  const style = {
    border: '2px solid black',
    padding: '16px',
  };
  return (
    <div style={style}>
      {children}
    </div>
  )
}

export default Wrapper;
```

<br />

## 중첩된 여러 component에 state 전송하는 방법
1. 하위 컴포넌트에 전달하 듯 props 반복
2. Context
3. Redux

<br />

### 2. Context 문법으로 props 없이 state 공유

```jsx
(App.js)

import { useState, useContext } from 'react';

let stockContext = React.createContext();

function App() {
  let [stock, setStock] = useState([1, 2, 3]);

  return (
    ...
  )
}
```
같은 state값을 공유하기 위해선 `createContext()` 함수를 이용해서 변수를 만들어야 한다. 그 변수는 특별한 `<컴포넌트>`가 된다.

```jsx
(App.js)

import { useState, useContext } from 'react';

let stockContext = React.createContext();

function App() {
  let [stock, setStock] = useState([1, 2, 3]);

  return (
    <>
      <stockContext.Provider value={stock}>
        <state를공유할컴포넌트 />
      </stockContext.Provider>
    </>
  )
}
```
위에서 만든 특별한 컴포넌트로 state 값을 공유할 컴포넌트들을 `<범위변수></범위변수>` 로 전부 감싸고 속성에 `value={state이름}`을 넣어 공유할 state를 전달하면 된다.

그렇게 되면 `<범위변수></범위변수>` 안에 있는 모든 HTML과 컴포넌트는 해당 state를 이용할 수 있다.

```jsx
(App.js)

import { useState, useContext } from 'react';

function state를공유할컴포넌트() {
  let stock = useContext(stockContext);

  return (
    ...
  )
}
```
마지막으로 `useContext()`라는 Hook을 이용해서 사용을 원하는 context를 불러와야 한다. 변수 `stock`은 stockContext에 들어있는 state를 담고 있게 되고, 그걸 통해 state를 사용할 수 있다.

Component 구조가 간단하다면 props를 쓰는게 더 편할 수 있다. Context는 Component가 복잡해질수록 편하다.


```jsx
(App.js)

import { useState, useContext } from 'react';

let stockContext = React.createContext();

function App() {
  let [stock, setStock] = useState([1, 2, 3]);

  return (
    <>
      <stockContext.Provider value={stock}>
        <state를공유할컴포넌트 />
      </stockContext.Provider>
    </>
  )
}

function state를공유할컴포넌트() {
  let stock = useContext(stockContext);

  return (
    ...
    <Test />
  )
}

function Test() {
  return <p> state </p>
}
```
하위의 하위 컴포넌트(Test)를 만든다고 가정해보자.

간단히 Context 문법을 요약하자면
1. `React.createContext()` 로 범위 설정하기
2. 전송을 원하는 컴포넌트를 `<범위 value={state명}> </범위>`로 감싸기
3. state 사용을 원하는 컴포넌트는 `useContext(범위)`를 이용

1, 2 번은 이미 세팅이 됐기 때문에 3번만 하면 된다.

```jsx
(App.js)

import { useState, useContext } from 'react';

let stockContext = React.createContext();

function App() {
  let [stock, setStock] = useState([1, 2, 3]);

  return (
    <>
      <stockContext.Provider value={stock}>
        <state를공유할컴포넌트 />
      </stockContext.Provider>
    </>
  )
}

function state를공유할컴포넌트() {
  let stock = useContext(stockContext);

  return (
    ...
    <Test />
  )
}

function Test() {
  let stock = useContext(stockContext); // Here!
  return <p> stock : {stock} </p>
}
```
처음 세팅만 귀찮을 뿐 useContext 받아오는 코드 한 줄이면 state를 간단히 받아와서 사용할 수 있다.

<br />

#### 컴포넌트가 다른 파일에 있을 경우
컴포넌트가 다른 파일에 있을 경우에도 사용법 똑같지만, 세팅이 하나 더 필요하다.

```jsx
(App.js)

let stockContext = React.createContext();

function App(){
  let [stock, setStock] = useState([1,2,3]);

  return (
    ...
    <stockContext.Provider value={stock}>
      <Other />
    </stockContext.Provider>
  )
}
```
```jsx
(Other.js)

function Other(){
  let 재고 = useContext(재고context);  // Error !

  return (
    ...
    <stockContext.Provider value={stock}>
      <Other />
    </stockContext.Provider>
  )
}
```
Other.js에서 useContext를 사용하려고 하면 정의되지 않았다고 에러가 뜬다.(App.js에 있으니까)

간단하게 변수를 App.js에서 export하고, Other.js에서 import해주면 된다.

```jsx
(App.js)

export let stockContext = React.createContext();

function App(){
  let [stock, setStock] = useState([1,2,3]);

  return (
    ...
    <stockContext.Provider value={stock}>
      <Other />
    </stockContext.Provider>
  )
}
```
```jsx
(Other.js)

import {stockContext} from './App.js';

function Other(){
  let 재고 = useContext(재고context);

  return (
    ...
    <stockContext.Provider value={stock}>
      <Other />
    </stockContext.Provider>
  )
}
```

> export 키워드는 변수나 함수 선언 왼쪽에 작성하면, 다른 파일에서 `import {변수명 혹은 함수명}` 로 가져와서 쓸 수 있다.



<br />
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)