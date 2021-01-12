# Ajax 
Ajax 요청은 쉽게 말해 서버에게 요청할 때, 새로고침없이 할 수 있게 도와주는 일종의 코드이다. 일부 개발환경에서는 jQuery 설치해서 ajax를 이용하는데, 리액트 사용자들은 조금 더 가벼운 axios 라이브러리를 설치하거나, fetch라는 바닐라자바스크립트 함수를 사용한다.

## What is Ajax
서버는 누군가가 요청을 하면 데이터를 서빙해주는 프로그램이라고 생각하면 쉽다. 예를 들어 google.com으로 요청하면 google 메인 페이지를 갖다주는 프로그램일 뿐이다.

서버에 요청하는 방법은 크게 두가지가 있다.
1. GET : 데이터, 웹페이지를 읽고 싶을 때 하는 요청
2. POST : 데이터를 서버로 보내고 싶을 때 하는 요청

GET 요청은 브라우저 주소창에 google.com을 입력하면 그게 GET요청을 하는 것이다. 구글의 특정 페이지를 서빙해달라고 GET 요청을 한 것이다.

원래 GET, POST 요청을 하게되면 새로고침이 되지만, Ajax는 GET,POST 이런걸 새로고침 없이 할 수 있게 도와주는 코드이다. 

<br />

## axios 설치
```powershell
yarn add axios
```
```powershell
npm install axios
```
먼저, axios 설치를 한다.

```jsx
import axios from 'axios';
```
axios를 import 한다.


<br />

## 더보기 버튼 만들기
더보기 버튼을 만들어서 `onClick` 시 서버에 새로운 상품데이터를 달라고 요청하는 기능을 개발해보자.

```jsx
(App.js)
function App() {
  return (
    <>
      ...
      <button onClick={ () => { 

        axios.get('GET요청할URL');

       } }>더보기</button>
    </>
  )
}
```
`axios.get()`이라고 작성하면 GET 요청을 새로고침없이 할 수 있다. GET 요청을 할 URL은 괄호안에 문자열로 넣으면 된다. 해당 URL은 보통 서버개발자에게 물어본다.

```jsx
(App.js)
function App() {
  return (
    <>
      ...
      <button onClick={ () => { 

        axios.get('http://lightix.blahblah/data2.json');

       } }>더보기</button>
    </>
  )
}
```
버튼이 클릭될 때마다 URL에 있는 json 데이터를 가져오게 된다.

```jsx
(App.js)
function App() {
  return (
    <>
      ...
      <button onClick={ () => { 

        axios.get('http://lightix.blahblah/data2.json')
        .then( () => { 요청에 성공하면 실행할 코드 } )
        .catch( () => { 요청에 실패하면 실행할 코드 } )

       } }>더보기</button>
    </>
  )
}
```
`get()` 함수 뒤에 `then()`, `catch()` 함수를 붙일 수 있는데, 각각 요청에 성공했을 때, 실패했을 때 실행할 코드를 담을 수 있다.

```jsx
(App.js)
function App() {
  return (
    <>
      ...
      <button onClick={ () => { 

        axios.get('http://lightix.blahblah/data2.json')
        .then( (result) => { console.log(result.data) } )
        .catch( () => { 요청에 실패하면 실행할 코드 } )

       } }>더보기</button>
    </>
  )
}
```
`then()` 함수 안에 콜백함수에 파라미터를 추가하면 그게 해당 URL을 통해 받아온 데이터이다. 
> 그 데이터 안에는 데이터 뿐만 아니라 여러가지 정보들이 담겨있다.

> fetch() 문법도 axios와 비슷하다. fetch(요청할URL)을 쓰면 바로 GET 요청을 하게되고, 뒤에 then()을 붙일 수 있는 것도 똑같다. 하지만 가져온 데이터가 JSON이면 object로 자동 변환이 안된다. 자세한건 나중에 알아보자


```jsx
function App(){
  let [product, setProduct] = useState(Data);

  return (
    <div>
      ...
      {
        product.map((a, i)=>{
           return <Card product={product[i]} i={i} key={i} />
        });
      }

      <button onClick={ () => { 

        axios.get('http://lightix.blahblah/data2.json')
        .then( (result) => { console.log(result.data) } )
        .catch( () => { 요청에 실패하면 실행할 코드 } )

       } }>더보기</button>

    </div>
  )
}
```
기존에 작성했던 map함수를 통해 product라는 state의 갯수만큼 `<Card>`를 생성해달라고 코드를 작성했었다. `map()`은 반복될테니 그럼 product라는 state를 수정하면 알아서 `<Card>`가 생성될 것이다.

따라서 작성해야할 코드는 더보기버튼을 눌렀을 때,
1. ajax 요청을 통해 data 가져오기
2. ajax 요청에 성공하면 product라는 state에 추가하기

가 될 것이다.

```jsx
function App(){
  return (
    <div>
      ...
      <button onClick={ () => { 

        axios.get('http://lightix.blahblah/data2.json')
        .then( (result) => { setProduct([...product, ...result.data]) } )
        .catch( () => { 요청에 실패하면 실행할 코드 } )

       } }>더보기</button>

    </div>
  )
}
```
전에 배웠던 state 사본만들고 사본을 바꾸는 형식이 아니라 한번에 처리했다. 

> `[...product, ...result.data]`
> product라는 state 데이터의 괄호를 벗겨서 추가하고,
> result.data라는 데이터도 괄호를 벗겨서 추가하고,
> 그 두 데이터를 []로 감싸서 하나의 array로 만들어달라.
는 코드이다.

<br />

### POST 요청
데이터를 받아오는 게 아니라 서버로 전송해야 할 때도 있다. 로그인할 때, 검색할 때, 게시물을 발행할 때 등.

서버로 데이터를 전송하기 위해선 POST 요청을 해야하는데, POST 요청은 데이터 전송할 URL과 전송할 데이터를 입력할 수 있다.

```jsx
axios.post('http://lightix.blahblah/data2.json', { id : 'test', pw : 1234})
  .then((result)=>{  })
  .catch(()=>{ })
```
`get()` 대신 `post()`를 사용하고, URL 옆에 두번째 파라미터로 원하는 데이터를 입력하면 된다. 마찬가지로 then과 catch도 사용할 수 있다.

<br />

### 여러가지 질문

> Q) 페이지를 방문하자마자 Ajax요청을 하고싶으면?
> 
> A) useEffect() 함수 안에 axios.get()을 하면 된다.

> Q) 로딩하는 동안만 UI 나타나게 하려면?
> 
> A) 기본적으로 state에 UI 상태를 담아두고 조건부 렌더링을 하면 된다. axios 전에, 로딩중 UI 띄워주는 코드를 작성하고, then에 로딩중 UI를 없애는 코드를 작성한다. catch에도 로딩중 UI를 없애는 코드와 실패 UI를 띄워주는 코드를 작성하면 된다.

> Q) 더보기 상품이 모두 끝났는데, 사용자가 버튼을 계속 누르면?
> 
> A) 보여줄 상품의 마지막에 도달했을 때, 버튼을 숨기고, 마지막이라고 알려주면 된다.

> Q) 더보기 클릭시 요청하는 json을 클릭할 때마다 바꾸고 싶다면?
> 
> A) axios.get()안에 URL을 하드코딩하지 않고, 버튼을 누를때마다 URL이 바뀌도록 코드를 작성하면 된다.







<br />
<br />
<br />

##### 출처
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)