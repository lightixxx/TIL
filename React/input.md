# input 다루기

<br />

## 사용자가 입력한 데이터를 state로 저장하는 법
사용자가 input에 입력한 데이터는 주로 중요한 데이터이기 때문에 state로 저장해서 쓰는 것이 일반적이다. 저장을 하기 위해서는 빈 state가 필요하다.
```jsx
function App() {
  let[inputValue, setInputValue] = useState('');

  return (
    <div>
      ...
    </div>
  )
}
```
초기값은 따옴표 두 개로 빈 문자열을 입력해주면 된다.
> state 초기값으로 무엇을 담을지 모르겠으면 빈 문자열이나 빈 array 이런걸 담으면 된다.

<br />

## 사용자가 input에 입력한 값 알아내는 법
input에 입력한 값을 알고싶으면 input에 onChange 이벤트핸들러를 달면된다.
```jsx
function App() {
  let[inputValue, setInputValue] = useState('');

  return (
    <div>
      <input onChange={ (e) => { console.log(e.target.value) } } />
    </div>
  )
}
```
`onChange` 는 input에 무언가를 입력할 때마다 특정 함수를 동작시키고 싶을 때 사용한다. 즉, input에 어떤 값이 입력될 때마다 `console.log(e.target.value)`를 실행하라고 적은 것이다.

`e.target`은 바닐라자바스크립트 문법으로 '지금 이벤트가 동작하는 HTML요소'를 뜻하고, `.value`는 input 등에 입력한 값을 의미한다.

<br />

## input에 값을 입력할 때마다 해당 값을 state에 저장
```jsx
function App() {
  let[inputValue, setInputValue] = useState('');

  return (
    <div>
      <input onChange={ (e) => { setInputValue(e.target.value) } } />
    </div>
  )
}
```
`inputValue`라는 state를 변경할 땐 `setInputValue()`함수를 쓸 수 있으니 `e.target.value`를 담았다. 그럼 이제 input에 뭔가 입력될 때마다 `inputValue`이라는 state가 `e.target.value`로 변경된다.


---

## input을 통해 새로운 글 작성하기
```jsx
function App() {
  let [글제목, 글제목변경] = useState(['W.I.P', 'STUDY', 'LOVE']);
  return(
    <div>
      <input />
      <button>저장</button>
    </div>
  )
}
```
현재 `[글제목]`이라는 state에 모든 글제목이 저장되어있다.
저장버튼을 누르면 `[글제목]`이라는 state에 input에 입력했던 값으로 제목 하나를 추가하면 기능 개발 끝이다. 

일단, 사용자가 input에 뭔가 입력하면 그 값을 state로 저장한다. 그리고 저장버튼을 누르면 그 state를 `[글제목]`이라는 배열에 추가하면 된다.

<br />

### 사용자가 input에 뭔가 입력하면 그 값을 변수나 state에 저장하기
```jsx
function App() {
  let [글제목, 글제목변경] = useState(['W.I.P', 'STUDY', 'LOVE']);
  let [입력값, 입력값변경] = useState('');
  return(
    <div>
      <input onChange={ (e)=>{ 입력값변경(e.target.value) } } />
      <button>저장</button>
    </div>
  )
}
```
입력값이라는 state를 하나 만들고, input에 뭔가 입력할 때, state로 저장되도록 기능개발을 했다. 그럼 input에 값을 입력할 때마다 입력값이라는 state에 실시간으로 저장된다.

<br />

### 버튼을 누르면 입력값 state를 [글제목]에 추가하기
```jsx
function App() {
  let [글제목, 글제목변경] = useState(['W.I.P', 'STUDY', 'LOVE']);
  let [입력값, 입력값변경] = useState('');
  return(
    <div>
      <input onChange={ (e)=>{ 입력값변경(e.target.value) } } />
      <button onClick={ ()=>{ 글제목변경(???) } }>저장</button>
    </div>
  )
}
```
`글제목변경()` 함수를 써서 변경해야 하는데 기본의 글제목을 모두 가져오는 것 보다는 복사를 해서 내용을 추가하자.

```jsx
function App() {
  let [글제목, 글제목변경] = useState(['W.I.P', 'STUDY', 'LOVE']);
  let [입력값, 입력값변경] = useState('');
  return(
    <div>
      <input onChange={ (e)=>{ 입력값변경(e.target.value) } } />
      <button onClick={ ()=>{

        const titleCopy = [...글제목];
        titleCopy.unshift(입력값);
        글제목변경(titleCopy);

      } }>저장</button>
    </div>
  )
}
```
`글제목`이라는 state를 수정해서 `글제목변경()`에 넣어야하는데 수정하는 방법은 `unshift()`라는 함수를 쓰면 된다. `글제목` state는 직접 수정하지 않고 복사해서 수정한다. 
1. 글제목을 복사해서 titleCopy라는 복사본을 만들고,
2. titleCopy를 수정하고,
3. titleCopy를 새로운 글제목이 되도록한다.

<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)