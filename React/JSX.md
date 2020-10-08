# JSX
A syntax extension to JavaScript

자바스크립트에 XML과 HTML을 더한 문법이다.

```jsx
const element = <h1>Hello, World!</h1>
```

JSX를 쓰는 것이 필수는 아니지만 편리하기 때문에 사용하는 것을 권장한다.
```jsx
// JSX 사용시
<div>Hello, {name}</div>

// JSX 미사용시
React.createElement('div', null, `Hello, ${name}`);
```

<br />

JSX를 사용하면 코드가 간결해지기 때문에 가독성이 향상되고, 버그를 발견하기 쉬워진다. 결과적으로는 개발 속도가 빨라진다. 또한 Injection Attacks를 방어할 수 있다.

## JSX는 하나의 객체를 나타낸다.
JSX는 하나의 객체로써 리액트는 이 객체를 읽어서 DOM을 만드는 데 사용하고, 항상 최신 상태를 유지한다. 

<br />

## JSX 사용법
JavaScript 코드와 XML/HTML 코드를 섞어서 사용하면 된다.
```jsx
<XML,HTML>
  {JavaScript 코드}
</XML,HTML>
```
<br />

### 값을 정의하는 법
큰 따옴표 사이에 문자열을 넣거나
```jsx
const element = <div tabIndex="0"></div>;
```
중괄호 사이에 JavaScript 코드를 넣으면 된다.
```jsx
const element = <img src={user.avatarUrl}>
```
<br />

### Children 정의하는 법
element는 무조건 하나의 태그로 전체를 감싸야 한다. 그렇지 않으면 에러가 난다.
```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```