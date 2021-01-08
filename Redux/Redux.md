# Redux

컴포넌트가 많아질수록 props 전송하는 과정이 복잡해진다. Redux를 이용하면 **props없이 모든 컴포넌트가 state를 공유해서 사용**할 수 있기 때문에 많은 React 개발자들이 사용한다. 하지만 조사에 따르면 3년 내에 Redux를 안 쓴다는 개발자가 많다고 한다. Context API를 위주로 학습하되, Redux 사용법도 알아주는 것이 좋겠다.

<br />

## Install
```shell
npm install redux react-redux
```
```shell
yarn add redux react-redux
```
redux와 react-redux 두개의 라이브러리를 설치해준다.
redux는 데이터를 엄격하게 관리하는 기능이고, react-redux는 리덕스를 리액트에서 쓸 수 있게 도와주는 기능을 제공한다.

<br />

## Setting
redux를 이용한 개발환경을 세팅하기 위해선 index.js에 다음과 같이 작성해야한다.
```jsx
(index.js)

import {Provider} from 'react-redux';

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>

);
```
1. `<Provider>를 import한다.
2. state 값 공유를 원하는 컴포넌트를 감싸준다.
     * App 컴포넌트를 감쌌기 때문에 App 컴포넌트와 그 안에 있는 HTML, 컴포넌트들 전부 state를 props 전송없이 사용할 수 있게 된다.

3. redux에서 state를 하나 만들기 위해서 `createStore()`를 써야한다.

```jsx
(index.js)

import { createStore } from 'redux';

let store = createStore( () => { 
  return [

    {id : 0, name : 'love', quan : 3}
    
    ]
  })

```
import해온 후 `createStore(callback function)`을 작성한다. 콜백함수에는 원하는 state의 초기값을 return하면 된다.

4. `<Propvider>`에 만든 state를 props처럼 등록하면 된다.

<br />

## store에 있는 state 데이터 꺼내는 방법
먼저 장바구니 컴포넌트를 만든다.
```jsx
(Cart.js)

import React from 'react';
import { Table } from 'react-bootstrap';

function Cart(){
  return (
    <div>
      <Table responsive>
        <tr>
          <th>#</th>
          <th>상품명</th>
          <th>수량</th>
          <th>변경</th>
        </tr>
        <tr>
          <td>1</td>
          <td>Table cell</td>
          <td>Table cell</td>
          <td>Table cell</td>
        </tr>
      </Table>
    </div>
  )
}

export default Cart;
```
react-bootstrap에서 Table을 가져와서 **store안에 있는 데이터를 props의 형태로 등록한 후 장바구니용 데이터를 바인딩**하면 된다. 

```jsx
(Cart.js)

import {connect} from 'react-redux';

function Cart(){
  return (
    <div>
      <Table responsive>
        ...
      </Table>
    </div>
  )
}

function state를props화한다는내용의함수명(state){
  return {
    state
  }
}

export default connect(state를props화한다는내용의함수명)(Cart);
```
1. `connect`함수를 import 한다.
2. 장바구니 데이터를 사용하기 원하는 컴포넌트 파일 밑에 함수를 만든다.
   * store 안에 있는 state를 props로 만드는 역할을 한다. `return` 안에 `{ 아무개: state }`를 하면 store 안에 있던 모든 state 데이터가 props로 등록이 된다. 키와 밸류가 같다면 `{state}`만 작성해도 무방하다. 혹은 `{스테이트이름: state.name, 스테이트아이디: state.id}`처럼 각각 등록해도 된다.
3. `export default` 하던 부분에 `connect()()`를 작성한다.
   * connect 함수에 인자로 `state를props화한다는내용의함수명`을 넣어준다. 이유는 모르겠고 react-redux 라이브러리의 사용법이다. 그리고 Cart 컴포넌트를 뒤에 소괄호에 넣어준다. 그럼 redux store에 있는 데이터들이 props로 엮인 채 컴포넌트가 export된다.

```jsx
(Cart.js)

import ...;
import {connect} from 'react-redux';

function Cart(props){
  return (
    <div>
      <Table responsive>
        ...
          <td>{props.state[0].name}</td>
        ...
      </Table>
    </div>
  )
}

function state를props화한다는내용의함수명(state){
  return {
    state
  }
}

export default connect(state를props화한다는내용의함수명)(Cart);
```
props를 쓰는 방법과 마찬가지로 파라미터에 props를 추가하면 된다. 필요한 곳에서 아까 등록한 props이름을 쓰면 된다.

<br />

## Summary

### setting
1. redux와 react-redux를 설치한다.
2. index.js에 `<Provider>`를 import한다.
3. state 값 공유를 원하는 컴포넌트를 감싸준다.
4. createStore를 import한다.
5. state를 만들어 let store에 저장한다.
6. `<Provider store={store}>`로 store를 등록하면 감싸진 컴포넌트들은 모두 store 안에 있는 값을 props없이 공유한다.

### state 사용법
1. 원하는 컴포넌트 파일에서 함수를 만들고 state를 props로 등록한다.
2. 제일 마지막에 `export default connect()()`한다.


<br />
<br />
<br />

##### 출처
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)




