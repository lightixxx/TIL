# useEffect

컴포넌트는 Lifecycle이라는 개념을 갖고 있다. 
useEffect라는 Hook은 컴포넌트가 마운트 됐을 때(처음 나타났을 때), 언마운트 됐을 때(사라질 때), 업데이트될 때(props가 바뀔 때) 특정 작업을 처리하는 방법이다.

## Lifecycle Hook
기존의 class 문법에서 만든 컴포넌트에서 사용가능했다.
```jsx
class Detail extends React.Component {
  conponentDidMount() {
    // Detail 컴포넌트가 Mount되고 나서 실행
  }
  componentWillUnmount() {
    // Detail 컴포넌트가 Unmount 되기 전에 실행
  }
}
```
기본적으로 가장 유용한 Hook은 
1. `conponentDidMount()` - 컴포넌트가 처음 만들어지고 실행할 코드
2. `componentWillUnmount()` - 다른 페이지로 넘어가는 등의 이유로 컴포넌트가 사라질 때, 그 전에 실행할 코드

<br />

## function 컴포넌트에서 사용하는 useEffect Hook
요즘엔 더 짧고 쉬운 useEffect를 더 많이 사용한다.
uesEffect를 import한 뒤, function 컴포넌트 안에 return 나오기 전에 적어주면 된다.
```jsx
import React, {useState, useEffect} from 'react';

function Detail(){
  useEffect(()=>{
    
  });
}
```
uesEffect 안에는 Detail 컴포넌트가 처음 생성되고 나서 실행하고 싶은 코드를 콜백함수에 넣어준다.

> useEffect() 내 코드는 컴포넌트가 첫 등장해서 로딩이 끝난 후(mount 끝났을 때), 재렌더링 되고난 후(update 되고난 후)에 실행된다. 즉, 컴포넌트가 로드됐을 때, 업데이트 됐을 때 실행하고 싶은 코드가 있으면 적으면 된다.

<br />

## 컴포넌트가 사라질 때 코드를 실행하고 싶으면
```jsx
import React, {useState, useEffect} from 'react';

function Detail(){

  useEffect(()=>{
   
    return function 함수명() { 
      // 컴포넌트가 사라질 때 실행되는 코드
    } 
  });
  
  return (
    ...
  )
}
```
useEffect 안에 return을 넣을 수 있는데, return 뒤에는 함수가 온다. 여기에 넣은 함수는 컴포넌트가 사라질 때 실행된다.

<br />

## 여러 개를 사용하고 싶을 때
```jsx
import React, {useState, useEffect} from 'react';

function Detail(){

  useEffect(()=>{
   // 첫번째로 실행
  });
  
  useEffect(()=>{
   // 두번째로 실행
  });

  return (
    ...
  )
}
```
useEffet는 여러개 적을 경우 위에서 부터 순서대로 실행된다.

<br />

## 업데이트될 때 useEffect 실행 막기
```jsx
useEffect(() => {
  
}, [state명]);
```
useEffect 함수 끝에 state를 넣을 수 있는데, 해당 state가 변경될 때만 업데이트라고 생각하고 실행해 달라고 해석할 수 있다. 그렇게 되면 저 코드에서는 컴포넌트가 로드될 때, 해당 state가 변경될 때만 실행된다. 대괄호 안에는 state를 여러개 넣을 수도 있다.

```jsx
useEffect(() => {
  
}, []);
```
[]안에 아무것도 넣지 않은 경우는 컴포넌트가 업데이트될 때 실행되지 않는다. 즉 컴포넌트가 로드될 때 딱 한만 실행하고 싶을 때 []대괄호 안을 비워두면 된다.

<br />

### 페이지 방문 후 3초 뒤에 사라지는 alert박스
전에 [UIPattern](https://github.com/lightixxx/TIL/blob/master/React/UIPattern.md)에서 UI를 만드는 법에 대해 배운 적이 있다.

1. UI가 보이는지 안보이는지 상태를 state로 저장한다.
2. state가 true일 때만 UI를 보여준다고 조건부 렌더링을 적는다.

```jsx
function Detail() {
  let [alertBox, setAlertBox] = useState(true);

  useEffect(() => {
    
  });
  return (
    ...
    {
      alertBox === true
      ? <div className="alert-box"></div>
      : null;
    }
  )
}
```
해당 UI의 상태를 state로 저장하고, 그 state를 통해 조건에 따라 렌더링이 되도록 했다.

```jsx
function Detail() {
  let [alertBox, setAlertBox] = useState(true);

  useEffect(() => {
    
  });
  return (
    ...
    {
      alertBox === true
      ? <div className="alert-box"></div>
      : null;
    }
  )
}
```
useEffect를 통해 컴포넌트가 로드되고 3초 후에 사라지게 만들어보자.
```jsx
function Detail() {
  let [alertBox, setAlertBox] = useState(true);

  useEffect(() => {
    const alertBoxTimer = setTimeout(() => {
      setAlertBox(false);
    }, 3000)
  });
  return (
    ...
    {
      alertBox === true
      ? <div className="alert-box"></div>
      : null;
    }
  )
}
```

<br />

### 업데이트가 될때도 실행되는 문제 해결
useEffect는 컴포넌트가 생성되고 업데이트 될 때 항상 실행된다. 업데이트될 때는 실행되지 않도록 useEffect에 두번째 파라미터로 빈 배열을 넣어야 한다.
```jsx
function Detail() {
  let [alertBox, setAlertBox] = useState(true);

  useEffect(() => {
    const alertBoxTimer = setTimeout(() => {
      setAlertBox(false);
    }, 3000)
  }, []); // 여기!

  return (
    ...
    {
      alertBox === true
      ? <div className="alert-box"></div>
      : null;
    }
  )
}
```
이제 useEffect는 업데이트가 될 때마다 실행되는 것이 아니라, 처음 컴포넌트가 로드될 때만 실행된다.

<br />

### setTimeout이 실행되기 전에 페이지를 벗어나면?
지금은 간단한 코드라 별도의 문제가 생기진 않지만, 코드가 길어질 경우 남아있는 타이머때문에 의도치 않은 상황이 생길 수 있기 때문에, 컴포넌트가 사라질 때 타이머를 없애는 코드도 추가해줘야한다.
```jsx
function Detail() {
  let [alertBox, setAlertBox] = useState(true);

  useEffect(() => {
    const alertBoxTimer = setTimeout(() => {
      setAlertBox(false);
    }, 3000);

    return () => { clearTimeout(alertBoxTimer) };
  }, []);

  return (
    ...
    {
      alertBox === true
      ? <div className="alert-box"></div>
      : null;
    }
  )
}
```
useEffect 안에 `return 함수`를 추가하면 컴포넌트가 사라질 때 함수를 실행시키기 때문에 `return clearTimeout`을 추가했다.


<br />
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)