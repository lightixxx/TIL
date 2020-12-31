# React-route-dom
간단히 말해 리액트에서 여러가지 페이지를 만들어서 나눌때 사용하는 라이브러리이다.

<br />

## install

```bash
yarn add react-route-dom
```
```bash
npm install react-route-dom
```
yarn 혹은 npm으로 react-route-dom을 설치를 해준다

```jsx
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <App/>
    </BrowserRouter>
  </React.StrictMode>
  document.getElementById('root')
);
```
설치가 끝나고 index.js을 열어서 BrowserRouter를 import하고, `<App>`컴포넌트를 `<BrowserRouter></BrowserRouter>` 로 감싸준다.

> ### HashRouter
> HashRouter는 사이트 방문시 URL 맨 뒤에 /#/이 붙는다.
> - 브라우저 주소창에 페이지를 입력하면 서버에게 특정 페이지를 보여달라고 요청하게 된다. 잘못해서 없는 페이지를 서버에 요청해서 404 에러가 뜨는 것을 방지하기 위해 #을 붙인다.(# 뒤에 붙은 것은 절대 서버로 요청되지 않기 때문) 하지만 지금은 요청할 서버없이 리액트가 라우팅을 담당하고 있다.
> - 따라서 BrowserRouter를 쓰려면 "이런 경로로 들어오는 요청은 리액트 메인페이지로 보내!" 혹은 "이런 경로로 들어오는 요청은 404 말고, 리액트가 라우팅해!" 라고 API를 짜야한다.

<br />

### 라우팅하기

라우팅을 하기 위해선 여러가지 태그들을 import 해야한다.
```jsx
(App.js)
import { Link, Route, Switch } from 'react-route-dom';

function App() {
  return (
    <div>
      ...
    </div>
  )
}
```
원하는 곳에 `<Route></Route>` 태그를 작성하고, `<Route>` 안에 path와 path 방문시 보여줄 HTML을 적어준다.
```jsx
(App.js)
import { Link, Route, Switch } from 'react-route-dom';

function App() {
  return (
    <div>
      <Route path="/">
        <h3>메인 페이지</h3>
      </Route>

      <Route path="/detail">
        <h3>상세 페이지</h3>
      </Route>
    </div>
  )
}
```
이제 / 으로 접속하면 '메인 페이지'가 뜨고, /detail 로 접속하면 '상세 페이지' 가 뜬다. 지금은 간단한 예로 작성했지만, `<h3>` 태그 말고 각 페이지에 해당하는 HTML을 컴포넌트화해서 넣어주면 라우팅 끝이다.

```jsx
<Route path="/detail" component={Detail}></Route>
```
컴포넌트라면 이렇게 넣어줄 수도 있고,
```jsx
<Route path="/detail"> <Detail /> </Route>
```
이렇게 넣어줄 수도 있다.

#### React-Router는 각각 다른 HTML을 보여주는 것이 아니라, HTML 내부의 내용을 바꿔서 다른 페이지처럼 보이게 하는 것이다.

<br />

## exact
위 코드에서 /detail로 접속하면 메인 페이지도 함께 나온다. 그 이유는 /detail이라고 적으면 / 라는 경로도 함께 포함되어 있어서 / 경로로 접속했다고 생각하고 메인페이지를, /detail로 접속했다고 생각하고 상세페이지를 보여주는 것이다. 
```jsx
<Route exact path="/" >
  <h3>메인 페이지</h3>
</Route>
```
/ 경로에 exact라는 속성을 부여하면 / 경로와 정확히 일치할 때만 메인페이지를 보여준다.

<br />

## 컴포넌트를 다른 파일에서 불러오기
```jsx
(Detail.js 파일)
import React from 'react';

function Detail() {
  return (
    <div>
      ...
    </div>
  )
}

export default Detail;
```
1. src 폴더에 Detail.js를 만든다.(컴포넌트 파일은 주로 대문자로 시작한다.)
2. import React를 해주고, 컴포넌트를 생성하는 코드를 담는다.
3. 마지막에 Detail이라는 함수를 export 해준다.

```jsx
(App.js 파일)
import Detail from './Detail.js';

function App() {
  return (
    <div>
      <Route path="/detail">
        <Detail />
      </Route>
    </div>
  )
}
```
App.js로 돌아와서 Detail을 import 하고 사용한다.

<br />

## Link (페이지 이동버튼 만들기)
Link 컴포넌트는 다른 주소로 이동시킨다. 리액트 라우터에선 일반적으로 `<a href="..."></a>` 를 사용하면 안되고 `<Link>` 컴포넌트를 사용해야한다.
```jsx
import { Link } from 'react-route-dom';

<Link to="/detail">Detail</Link>
```
페이지 이동버튼으로 바꾸기 원하는 글자를 `<Link>`태그로 감싸고 `to="??"` 속성을 통해 경로를 지정해주면 된다.

```jsx
(App.js 파일)

function App() {
  return (
    <div>
      <Navbar>
        <Nav.Link> <Link to="/">Home</Link> </Nav.Link>
        <Nav.Link> <Link to="/detail">Detail</Link> </Nav.Link>
      </Navbar>
    </div>
  )
}
```
그럼 Home을 누르면 / 경로로, Detail을 누르면 /detail 경로로 이동한다.

<br />

## Link 컴포넌트 없이 페이지 이동기능 만들기
`<Link>` 없이 코드 실행 중간에 페이지를 이동시키고 싶은 경우엔 페이지 이동 함수를 사용하면 된다.

뒤로가기 버튼을 만든다고 가정해보자.
```jsx
(Detail.js 파일)

import { useHistory } from 'react-router-dom';

function Detail() {
  let history = useHistory();

  return (
    <div>
      ...
      <button onClick={ () => { history.goBack() } }>뒤로가기</button>
    </div>
  )
}
```
1. useHistory를 import 한다.
2. `let history`에 useHistory 함수를 할당한다.
3. button에 onClick 이벤트핸들러로 `history.goBack()` (페이지가 뒤로감)을 달아준다. 

`useHistory()`는 일종의 Hook으로 객체가 들어있다. 그 객체 안에는 페이지 이동 내역과 유용한 메소드들이 저장되어 있다. 

커스텀 페이지로 이동하는 기능을 만들고 싶을 땐, `push()` 메소드에 인자로 이동 경로를 문자열로 넣어주면 된다.

> 라이브러리 사용법을 찾아서 읽거나 검색하면 많은 기능들이 나온다.

<br />

## Switch
매치되는 `<Route>`들을 전부 보여주지 말고 한번에 하나만 보여주길 원할 때 사용한다.
```jsx
(App.js 파일)

function App(){
  return (
    <div>
      <Route exact path="/">
        ...
      </Route>
      <Route path="/detail">
        <Detail/>
      </Route>
      <Route path="/:id">
        <div>/ 뒤에 모든 문자가 오면 여기로 열려라</div>
      </Route>
    </div>
  )
}
```
위 코드에서 /detail로 이동하면, `<Detail>` 뿐만 아니라 `<div>/ 뒤에 ...</div>` 이것도 같이 렌더링된다. 리액트 라우터는 그냥 URL 매치되는 것들 전부를 보여주기 때문이다. 여기서 :id는 임의로 적은 것이고, 밑에 URL 파라미터에서 다시 정리.

이걸 방지하고 한번에 하나의 `<Route>`만 보여주고 싶다면 모든 `<Route>`들을 `<Switch>`로 감싸면 된다.
```jsx
(App.js 파일)

function App(){
  return (
    <div>

      <Switch>
        <Route exact path="/">
          ...
        </Route>
        <Route path="/detail">
          <Detail/>
        </Route>
        <Route path="/:id">
          <div>/ 뒤에 모든 문자가 오면 여기로 열려라</div>
        </Route>
      </Switch>

    </div>
  )
}
```
이렇게 `<Switch>`로 감싸면 여러개의 Route가 매칭이 되어도 매칭된 것중 제일 위에 Route 하나만 보여준다. 

<br />

## URL 파라미터
라우터의 중요한 기능인 URL 파라미터는 'URL 뒤에 무슨 문자를 적든 여기로 안내해주세요' 라는 의미로 사용할 수 있는 URL 작명법이다. 

URL 주소가 /detail/0 으로 접속하면 0번째 상품의 상세페이지,/detail/1 로 접속하면 1번째 상품의 상세페이지, /detail/2 로 접속하면 2번째 상품의 상세페이지가 나오게 만든다고 가정해보자.

```jsx
<Route path="/detail/0">
  <Detail shoes={shoes}/>
</Route>
<Route path="/detail/1">
  <Detail shoes={shoes}/>
</Route>
<Route path="/detail/2">
  <Detail shoes={shoes}/>
</Route>
```
이런 식으로 각각의 `<Route>`를 만들어도 되겠지만, 개수가 많아진다면 노가다 그 자체이다. 반복문을 돌려야 할 것 같지만, 보통 URL을 만들 땐 반복문을 안쓰고 URL 파라미터 문법을 이용해 축약시켜서 사용한다.

```jsx
<Route path="/detail/:id">
  <Detail products={products}/>
</Route>
```
:id 자리에 아무 문자나 입력하면 `<Detail>`컴포넌트를 보여달라는 의미이다. 이제 /detail/1234 를 입력해도 `<Detail>` 컴포넌트를 보여준다.
- id라는 부분은 함수 파라미터처럼 자유롭게 작명하면 된다.
- 파라미터를 여러개 추가할 수도 있다.

<br />

`detail/???` 여기에 적은 파라미터를 이용해서 각각 다른 데이터를 바인딩해서 보여주면 해당 숫자에 따라 다른 상세페이지를 보여줄 수 있다.
```jsx
(Detail.js 파일)

function Detail(props) {
  return (
    <div>
      <h4>{props.products[:id자리에 있던 숫자].title}</h4>
      <p>{props.products[:id자리에 있던 숫자].content}</p>
      <p>{props.products[:id자리에 있던 숫자].price}원</p>
    </div>
  )
}
```
`[:id자리에 있던 숫자]`를 저곳에 넣고 싶다면 useParams()라는 훅을 사용하면 된다.
```jsx
(Detail.js 파일)
import { useParams } from 'react-router-dom';

function Detail(props) {
  let { id } = useParams();
  return (
    <div>
      <h4>{props.products[:id자리에 있던 숫자].title}</h4>
      <p>{props.products[:id자리에 있던 숫자].content}</p>
      <p>{props.products[:id자리에 있던 숫자].price}원</p>
    </div>
  )
}
```
1. useParams를 import한다.
2. 변수에 할당한다.
`useParams()`라는 함수는 현재 URL에 적힌 모든 파라미터를 {파라미터1, 파라미터2} 이런식으로 저장해주는 함수이다. 그걸 구조분해문법을 이용해 따로 변수로 빼서 할당한 것이다. 따라서 `id`라는 변수는 `:id자리에 있던 숫자`를 의미한다.

/detail/1로 접속하면 id라는 변수는 1이 되는 것이고, /detail/100으로 접속하면 id라는 변수는 100이 되는 것이다.
```jsx
(Detail.js 파일)
import { useParams } from 'react-router-dom';

function Detail(props) {
  let { id } = useParams();
  return (
    <div>
      <h4>{props.products[id].title}</h4>
      <p>{props.products[id].content}</p>
      <p>{props.products[id].price}원</p>
    </div>
  )
}
```
이것이 리액트에서 상세페이지를 만드는 패턴이다.

<br />

### 자료의 순서가 변경되면 상세페이지도 고장나는 문제
예를 들어 /detail/0으로 접속하면 0번째 상품이 나오는데, 다른 페이지에서 가격순으로 정렬을 해서 0번째 상품이 1번째 상품으로 변하게 되는 문제가 발생할 때, 해결하는 방법은?

> Detail.js에 데이터 바인딩할 때 0번째 상품의 제목을 보이게 했는데, 그게 아니라 상품의 영구번호가 0인 상품의 제목을 보여달라고 하면 된다. data.js를 열어보면 각 상품마다 id가 있다.

data.js 안에는 `{id: 0}` 이런 상품 각각의 영구 번호가 존재한다. 그럼 현재 `/:id자리에 입력한 값`과 영구번호가 같은 {상품데이터}를 찾아서 데이터바인딩하면 된다!

```jsx
(Detail.js 파일)
import { useParams } from 'react-router-dom';

function Detail(props) {
  let { id } = useParams();
  let itemId = props.products.find( (item) => {
    return item.id == id;
  })

  return (
    <div>
      <h4>{itemId.title}</h4>
      <p>{itemId.content}</p>
      <p>{itemId.price}원</p>
    </div>
  )
}
```
`find()`함수는 Array 안에서 원하는 자료를 찾고 싶을 때 사용하는 메서드이다. array 뒤에 붙일 수 있고, 안에는 콜백함수가 들어간다. 콜백함수의 파라미터는 array 안에 있는 하나 하나의 데이터를 의미하고, 조건식을 적어 참인 데이터만 `return` 해서 새로운 변수에 할당을 한다. 현재 URL의 /:id에 적힌 값과 상품의 영구번호(item.id)이 같은지를 조건식으로 비교한다.

그래서 /detail/0으로 접속했을 때, `itemId`를 출력해보면 item.id가 0인 데이터가 나온다. 따라서 itemId를 이용해서 상품명, 가격 등 HTML 부분에 데이터바인딩을 한 것이다.

실제 개발을 할 땐, 그냥 서버에서 해당 id값인 상품데이터를 Ajax로 요청할 것이다.(나중일..)


<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)