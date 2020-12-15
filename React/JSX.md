# JSX
A syntax extension to JavaScript
```jsx
const element = <h1>Hello, World!</h1>
```
JSX는 자바스크립트에 XML과 HTML을 더한 것으로 리액트에서 생김새를 정의할 때 사용하는 문법이다. 리액트 컴포넌트 파일에서 XML 형태로 코드를 작성하면 babel이 JSX를 JavaScript 문법으로 변환해준다.

JSX를 쓰는 것이 필수는 아니지만 편리하기 때문에 사용하는 것을 권장한다.
```jsx
// JSX 사용시
<div>Hello, {name}</div>

// JSX 미사용시
React.createElement('div', null, `Hello, ${name}`);
```
JSX를 사용하면 코드가 간결해지기 때문에 가독성이 향상되고, 버그를 발견하기 쉬워진다. 결과적으로는 개발 속도가 빨라진다. 또한 Injection Attacks를 방어할 수 있다.

또한 JSX는 하나의 객체로써 리액트는 이 객체를 읽어서 DOM을 만드는 데 사용하고, 항상 최신 상태를 유지한다. 

<br />

## JSX 사용법
JavaScript 코드와 XML/HTML 코드를 섞어서 사용하면 된다.
```jsx
<XML,HTML>
  {JavaScript 코드}
</XML,HTML>
```
<br />

### JSX의 기본 규칙
```jsx
import React from 'react';

function Hello() {
  return <div>Hello world!</div>;
}

export default App;
```
<br />

### 값을 정의하는 법
큰 따옴표 사이에 문자열을 넣거나,
```jsx
const element = <div tabIndex="0"></div>;
```
중괄호 사이에 JavaScript 코드를 넣으면 된다.
```jsx
function App() {
  const name = 'lightix';
  return (
    <h1>Hello, {name}!</h1>
  );
}
```
<br />

### Children 정의하는 법

1. 일반적으로 HTML에서는 `<input>`, `<br>`태그는 닫지않고 사용할 수 있지만 리액트는 무조건 닫아야 한다.

```jsx
function App() {
  return (
    <div>
      <input />
      <br />
    </div>
  );
}
```
<br />

2. element는 무조건 하나의 태그로 전체를 감싸야 한다. 그렇지 않으면 에러가 난다.
```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```
하지만 불필요하게 `<div>`를 생성하는 것이 스타일 설정을 할 때 복잡함을 유발할 수 있고, `<div>`로 감싸기 애매한 태그들도 있다. 그땐, 리액트의 Fragment를 사용하면 된다.
```jsx
function App() {
  return (
    <>
      <h1>Hello!</h1>
      <h2>Bye!</h2>
    </>
  );
}
```
위와 같이 태그를 작성할 때 이름없이 작성하게되면, Fragment가 생성되는데, 브라우저 상에서 별도의 엘리먼트로 나타나지 않는다.

<br />

### style과 className
1. inline-style은 객체 형태로 작성한다.
2. `font-size`와 같이 -로 구분된 것은 camelCase로 작성한다.
3. 기본 단위는 px이며, 다른 단위를 사용할 땐 문자열로 작성한다.
4. CSS 클래스를 설정할 땐, `class=` 가 아닌 `className=` 으로 작성한다.

```jsx
function App() {
  const name = 'react';
  const style = {
    backgroundColor: 'black',
    color: 'aqua',
    fontSize: 24,
    padding: '1rem'
  }

  return (
    <>
      <Hello />
      <div style={style}>{name}</div>
      <div className="container"></div>
    </>
  );
}
```

<br />

### 주석
JSX 내부의 주석은 `{/* 주석 */}` 처럼 작성하고, 열린 태그 내부에서는 `// 열린태그 내부의 주석` 로 작성할 수 있다.
```jsx
function App() {
  return (
    <>
      {/* 주석은 화면에 보이지 않습니다 */}
      /* 중괄호로 감싸지 않으면 화면에 보입니다 */
      <Hello 
        // 열리는 태그 내부
      />
    </>
  );
}
```

<br />
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)
- [소플](https://edu.goorm.io/learn/lecture/12976/%EC%B2%98%EC%9D%8C-%EB%A7%8C%EB%82%9C-react-%EB%A6%AC%EC%95%A1%ED%8A%B8/info)