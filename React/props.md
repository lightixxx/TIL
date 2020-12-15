# props
props 는 properties 의 줄임말로, 어떤 값을 컴포넌트에게 전달할 때 props를 사용한다.

<br />

## props의 기본 사용법
App 컴포넌트에서 Hello 컴포넌트를 사용할 때 `name`이라는 값을 전달해주고 싶다고 가정해보자.

```jsx
{/* App.js */}
import React from 'react';
import Hello from './Hello';

function App() {
  return (
    <Hello name="react" />
  );
}

exprot default App;
```
Hello 컴포넌트에서 name 값을 사용할 땐,
```jsx
{/* Hello.js */}
import React from 'react';

function Hello(props) {
  return <div>안녕하세요! {props.name}</div>
}

export default Hello;
```
props는 객체형태로 전달되며, `name`의 값을 조회하고 싶다면 `props.name`을 조회하면 된다.

<br />

## 여러개의 props, 비구조화 할당
props 내부의 값을 조회할 때 마다 `props.`을 입력하지 않고, 함수의 파라미터에서 비구조화 할당(구조분해) 문법을 사용해서 여러 개의 props를 간결한 코드로 작성할 수 있다. 
```jsx
import React from 'react';

function Hello({color, name}) {
  return <div style={{color}}> 안녕하세요 {name} </div>
}

export default Hello;
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
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)