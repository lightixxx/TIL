# Redux

컴포넌트가 많아질수록 props 전송하는 과정이 복잡해진다. Redux를 이용하면 **props없이 모든 컴포넌트가 state를 공유해서 사용**할 수 있기 때문에 많은 React 개발자들이 사용한다. 즉, '전역 상태'를 생성하고 관리하기 위한 라이브러리이다. 학습용으로 만드는 소규모 프로젝트에서는 당최 왜 이 복잡한 것을 써야하는지 모를 수 있지만, 실무에서 큰 규모의 프로젝트를 진행할 때 redux는 강력한 도구가 된다.

![Frame 3](https://user-images.githubusercontent.com/59480963/104291328-bf217780-54fe-11eb-9176-c94df916186e.jpg)
리덕스의 코어 컨셉은 크게 네가지만 기억하면 된다. 

component는 화면을 보여주는 view(App)이 될 것이고, store는 정보를 저장하는 공간이라고 생각하면 된다. 저장된 공간에서 component가 데이터를 가져와서 사용을 할 수 있게 하는 것이다. 
component에서 어떤 데이터가 변동이 일어나면, 그 값을 store로 업데이트 하기 위해 action과 reducer를 통해서 값을 관리한다. 
1. component에서 `dispatch()`를 통해 action으로 호출한다.
2. action에 정의돼있는 내용이 reducer에 의해서 handling이 된다.
3. handling에 따라서 상태 값이 update된다.
4. 업데이트된 내용을 subscribe를 통해서 component에 전달한다.

<br />

## vanilla JS에서 사용하기

### Install
```powershell
npm init -y
```
기본적인 옵션으로 package.json을 설치하고
```powershell
npm install redux
```
redux를 설치하고, store.js을 작성한다.
```jsx
// (store.js)
const redux = require('redux'); //redux를 불러오기
```

redux의 core concept에 따라 정리하면
```jsx
// (store.js)
const redux = require('redux'); // redux 불러오기
const createStore = redux.createStore; // createStore 함수를 변수에 할당
const ADD_FOLLOWER = 'ADD_FOLLOWER'; // reducer에서도 type이 반복되기 때문에 변수로 저장하는 것이 편하다.

// actions
// type이 ADD_FOLLOWER인 객체를 반환하는 action
const addFollower = () => {
  return {
    type: ADD_FOLLOWER
  }
}

// reducers
const initialState = {
  followers: 829 // 초기 state 값
}
// state와 action을 인자로 받아와서 조건에 따라 state를 return하는 reducer
const reducer = (state=initialState, action) => {
  switch(action.type) {
    case ADD_FOLLOWER: 
      return {
        ...state, // 기존의 state 값을 복사하고,
        followers: state.followers + 1, // follower에 1 증가시키기
      }
    default: return state;
  }
}

// store
// 인자로 reducer를 받는 createStore
const store = createStore(reducer);

// subscribe - view - dispatch
console.log(store.getState()); // getState()를 통해 {followers: 829}인 것을 확인
store.dispatch(addFollower()); // dispatch()에 action을 호출하면 reducer가 작동하면서, 값의 변동이 일어난다. 
console.log(store.getState()); // dispatch()가 일어난 후엔 {followers: 830}

// subscribe() 메소드를 통해 확인할 수도 있다. 
// 첫번째 인자로 함수를 받는다.
store.subscribe(() => {
  console.log(store.getState());
})
```

<br />

### createStore의 두번째 인자로 middleWare 넘기기

#### install
```powershell
npm install redux-logger
```
```jsx
const reduxLogger = require('redux-logger');
const looger = reduxLogger.createLogger();
const applyMiddleware = redux.applyMiddleware;

// store
const store = createStore(reducer, applyMiddleware(logger));
```

<br />

### 여러개의 reducer 넘기기
```jsx
const redux = require('redux');
const createStore = redux.createStore;
const ADD_FOLLOWER = 'ADD_FOLLOWER';
const ADD_VIEWCOUNT = 'ADD_VIEWCOUNT';
const combineReducer = redux.combineReducers; // 여러개의 reducer를 합쳐주는 메서드

// middleware를 위해 필요한 것
const reduxLogger = require('redux-logger');
const looger = reduxLogger.createLogger();
const applyMiddleware = redux.applyMiddleware;

// action
const addFollower = () => {
  return {
    type: ADD_FOLLOWER
  }
}

const addViewCount = () => {
  return {
    type: ADD_VIEWCOUNT
  }
}

// state가 여러 개가 생성되기 때문에 값에 맞는 변수명으로 변경
const followerState = {
  followers: 829
}

// reducer가 여러 개가 생성되기 때문에 state에 따른 reducer명으로 변경
const followerReducer = (state=followerState, action) => {
  switch(action.type) {
    case ADD_FOLLOWER: 
      return {
        ...state,
        followers: state.followers + 1,
      }
    default: return state;
  }
}

const viewState = {
  viewCount : 100
}

const viewReducer = (state=viewState, action) => {
  switch(action.type) {
    case ADD_VIEWCOUNT:
      return {
        ...state,
        viewCount: state.viewCount + 1
      }
    default : return state;
  }
}

const rootReducer = combineReducers({
  follower: followerReducer,
  view: viewReducer,
})

// store
// combine된 reducer를 넣을 수 있다.
const store = createStore(rootReducer);
```




<br />

## React에서 사용하기
React 프로젝트에서도 '어떻게 파일을 배치하는지'의 차이만 있을 뿐, 사실상  action, reducer, store 를 구조화 시켜서 사용하는 것은 같다.

### Install
```powershell
npm install redux react-redux
```
```powershell
yarn add redux react-redux
```
redux와 react-redux 두 개의 라이브러리를 설치해준다.
redux는 데이터를 엄격하게 관리하는 기능이고, react-redux는 리덕스를 리액트에서 쓸 수 있게 도와주는 기능을 제공한다.

<br />

### File setting
src 폴더안에 components들을 모아놓을 폴더를 생성하고, redux를 관리해줄 redux 폴더를 생성한 뒤 그 안에 store.js를 생성하고, action, reducer, type을 한 폴더에 넣은 뒤 각각 구분하기 위해 actions, reducer, types를 만들어준다.

<img width="185" alt="react-redux file setting" src="https://user-images.githubusercontent.com/59480963/104354932-4bf32200-554d-11eb-89a7-5f22967c01d0.png">

<br />




<br />

## coding apple 강의

### Setting
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
1. `<Provider>`를 import한다.
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
import해온 후 `createStore(callback function)`을 작성한다. 콜백함수에는 원하는 state의 초기값을 return하면 된다. `store`에는 전역 상태를 저장한다. 객체 형태로 저장이 되고, 리듀서를 통하지 않고는 접근할 수 없다. 하나의 어플리케이션에 하나의 저장소만 존재해야하기 때문에, 리액트에서는 주로 `index.js`에 정의한다.

4. `<Propvider>`에 만든 state를 props처럼 등록하면 된다.
```jsx
(index.js)

import {Provider} from 'react-redux';

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider store={store}>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>
);
```


<br />

### store에 있는 state 데이터 꺼내는 방법
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

### Summary

#### setting
1. redux와 react-redux를 설치한다.
2. index.js에 `<Provider>`를 import한다.
3. state 값 공유를 원하는 컴포넌트를 감싸준다.
4. createStore를 import한다.
5. state를 만들어 let store에 저장한다.
6. `<Provider store={store}>`로 store를 등록하면 감싸진 컴포넌트들은 모두 store 안에 있는 값을 props없이 공유한다.

#### state 사용법
1. 원하는 컴포넌트 파일에서 함수를 만들고 state를 props로 등록한다.
2. 제일 마지막에 `export default connect()()`한다.

<br />

### state 데이터를 수정하는 방법
1. `reducer` 함수를 만들고 그 곳에 데이터 수정하는 방법을 정의한다.
2. 원하는 곳에서 `dispatch()`를 써서 `reducer`에 써진대로 데이터를 수정한다.



<br />
<br />
<br />

##### 출처
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)
- [Code Scalper](https://youtu.be/wSbjROmXTaY)




