# Conditional Rendering (조건부 렌더링)
조건에 따라 다른 결과물을 렌더링할 수 있다.
App 컴포넌트에서 Hello 컴포넌트를 사용할 때, `isSpecial` props를 설정한다고 가정해보자.
```jsx
{/* App.js */}
import React from 'react';
import Hello from './Hello';
import Wrapper from './Wrapper';

function App() {
  return (
    <Wrapper>
      <Hello name="react" color="red" isSpecial={true}/>
      <Hello color="pink" />
    </Wrapper>
  )
}

export default App;
```
`true`는 자바스크립트 값이기 때문에 중괄호로 감싸주었다.
Hello 컴포넌트에서는 `isSpecial`이 `true`인지 `false`인지에 따라 컴포넌트 좌측에 💙를 렌더링해보자. 이를 처리하는 가장 기본적인 방법은 삼항연산자를 사용하는 것이다.
```jsx
{/* Hello.js */}
import React from 'react';

function Hello({ color, name, isSpecial }) {
  return (
    <div style={{ color }}>
      { isSpecial ? <b>💙</b> : null }
      안녕하세요 {name}
    </div>
  );
}

Hello.defaultProps = {
  name: '이름없음'
}

export default Hello;
```
`isSpecial`값이 `true`라면 `<b>💙</b>`를, `false`라면 null을 렌더링하도록 했다. JSX 문법에서는 `null`, `undefined`, `false`를 렌더링 하면 아무것도 나타나지 않는다.

보통 삼항연산자를 사용해서 조건부 렌더링을 할 땐, 특정 조건에 따라 보여줘야 하는 내용이 다를 때 사용한다. 위 코드의 경우 `true`일 땐 보여주고, `false`일 땐 안보이기 때문에 `&&`연산자를 사용하는 것이 더 간편하다
```jsx
{/* Hello.js */}
import React from 'react';

function Hello({ color, name, isSpecial }) {
  return (
    <div style={{ color }}>
      { isSpecial && <b>💙</b> }
      안녕하세요 {name}
    </div>
  );
}

Hello.defaultProps = {
  name: '이름없음'
}

export default Hello;
```
`{ isSpecial && <b>💙</b>}`의 결과는 `isSpecial`이 `false`일 땐 `false`이고, `isSpecial`이 `true`일 땐 `<b>💙</b>`가 된다.

<br />

또한 컴포넌트의 props 값을 생략하면 이는 `true`로 간주된다.
```jsx
{/* App.js */}
import React from 'react';
import Hello from './Hello';
import Wrapper from './Wrapper';

function App() {
  return (
    <Wrapper>
      <Hello name="react" color="red" isSpecial />
      <Hello color="pink"/>
    </Wrapper>
  );
}

export default App;
```
위 코드처럼 `isSpecial`만 넣게되면 `isSpecial={true}`와 같은 의미로 간주된다.

<br />
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)