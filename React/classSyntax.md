# class 문법
요즘은 잘 사용되지 않지만, 실무를 하다보면 옛날 문법으로 작성된 리액트파일을 볼 수 있기에 간단하게 알아보자.

## Function component VS Class component
function component는 function이고, 어떤 값을 return하고, screen에 표시한다. 반면 Class component는 class이지만, React.Component로부터 확장되고 screen에 표시하고, 그것을 render 메소드 안에 넣는다. react는 자동적으로 모든 class component의 render 메소드를 실행한다.

## Component
```jsx
function App() {
  return (
    <div>
      ...
      <Profile />
    </div>
  )
}

class Profile extends React.Component {
  constructor() {
    super();
  }

  render() {
    return (
      <div>프로필영역</div>
    )  
  }
}
```
class로 component를 만드는 기본적인 방법이다.
1. `class`를 하나 만들고 이름을 짓는다.
2. `React.Component`를 `extends` 한다.
3. `constructor(){}` 함수를 언급한다.
4. `render(){}`함수 안에 원하는 HTML을 작성한다.
5. 원하는 곳에 해당 클래스를 첨부한다.

> class는 데이터와 함수를 보관하는 덩어리라고 생각하면 된다. extends는 덩어리를 만들 때 오른쪽에 있는 것의 성질을 물려받아서 만들겠다고 하는 것이다. 위 코드에서 React.Component는 컴포넌트 성질을 갖고있는 덩어리이다. 그것을 extends 해서 class를 만들면 컴포넌트를 만들 수 있다.

class 문법은 여러개의 데이터나 함수를 한 곳에 보관하고 싶을 때 쓰는 문법으로, class를 만들면 class가 갖고있는 데이터를 복사해서 사용할 수 있는 object를 쉽게 만들 수 있다. 혹은 class가 갖고있는 데이터를 그대로 복사해서 사용할 수 있는 class도 extends 문법을 통해쉽게 만들 수 있다.

- react 개발자들이 컴포넌트와 관련된 데이터와 함수들을 보관하기 위해 React.Component라는 class를 만들었다.
- React.Component를 extends해서 복사하면 내 컴포넌트를 만들 수 있다.
- 그렇게 만들어진 컴포넌트는 리액트 관련 데이터와 함수를 자유롭게 쓸 수 있다.

<br />

## state
class 문법에서는 constructor 안에 모든 state를 보관한다.
```jsx
class Profile extends React.Component {
  constructor() {
    super();
    this.state = { name : 'lightix', age : 28 }
  }

  render() {
    return (
      <div>
        <h3>저는 {this.state.name } 입니다!</h3>
      </div>
    )  
  }
}
```
- state를 저장할 땐 `constructor`안에 `this.state`라는 변수에 모두 보관해야 한다.
- 꺼내서 쓸 때는 `this.state.state명` 으로 사용한다.

> constructor는 변수와 함수가 가득한 class 덩어리를 만들 때 새로운 변수를 넣는 공간이다. super()는 "extends 했던 React.Component 라는 덩어리에 있던 변수들을 그대로 쓰겠다."라는 의미이다. 반드시 super() 밑에 state를 만들어야 한다.

<br />

### state 값을 변경하는 법
버튼을 누를 때 이름을 'MoodwasH'로 변경하는 기능을 만들어보자.
onClick같은 것은 똑같지만, state를 변경할 때는 특정 함수를 써야한다.
```jsx
class Profile extends React.Component {
  constructor() {
    super();
    this.state = { name : 'lightix', age : 28 }
  }

  render() {
    return (
      <div>
        <h3> 저는 {this.state.name } 입니다! </h3>
        <button onClick={ () => { this.setState( {name: 'MoodwasH'} ) } }> 버튼 </button>
      </div>
    )  
  }
}
```
1. 버튼을 만들고 `onClick` 이벤트핸들러를 넣는다.
2. state를 변경할 땐 `this.setState()`라는 내장함수를 써야한다.
3. `this.setState()` 파라미터로 바꾸고 싶은 state 이름과 값만 적어주면 된다.

최신문법으로 만든 state 변경함수들은 state를 아예 바꾸는 역할을 하는데에 반해, `setState()`는 딱 필요한 부분만 수정하고 나머지는 건들지 않는다. 따라서 최신 문법에서 했던 state 복사본 만들어서 수정하고 변경하는 일을 할 필요가 없다.

<br />

## function
최신 문법에서는 함수를 어디에 만들어도 상관없는데, 이전 문법에서는 위치가 정해져있다.
```jsx
class Profile extends React.Component {
  constructor() {
    super();
    this.state = { name : 'lightix', age : 28 }
  }

  changeName() {
    this.setState({name: 'MoodwasH'})
  }

  render() {
    return (
      <div>
        <h3> 저는 {this.state.name } 입니다! </h3>
        <button onClick={ this.changeName }> 버튼 </button>
      </div>
    )  
  }
}
```
버튼에 있던 이름바꾸는 코드를 함수로 뺐다. 모든 커스텀 함수는 `constructor()`와 `render()` 사이에 작성하면 된다.

하지만 위 코드는 에러가 난다. 이유는 `this.setState()`의 `this`가 달라졌기 때문이다. 자바스크립트에선 `function(){}`을 쓰면 안에 있는 `this`의 값이 새로 재정의된다. 그래서 `this.setState()`에서 사용할 `this`값도 의도와는 다르게 변형된 것이다. 

따라서 `this`가 재정의되지 않게 함수를 사용할 때 `this.changeName.bind(this)`로 사용하거나, 아니면 함수를 아예 화살표함수로 바꾸면 된다.
```jsx
class Profile extends React.Component {
  constructor() {
    super();
    this.state = { name : 'lightix', age : 28 }
  }

  changeName = () => {
    this.setState({name: 'MoodwasH'})
  }

  render() {
    return (
      <div>
        <h3> 저는 {this.state.name } 입니다! </h3>
        <button onClick={ this.changeName }> 버튼 </button>
      </div>
    )  
  }
}
```

> ### 화살표함수와 this 키워드의 관계
> 화살표 함수를 사용하면 안에 있는 this값을 재정의해주지 않는다. 바깥에 있던 this의 값을 그대로 가져와서 사용하지만, function(){}을 사용하면 this값이 새롭게 변한다. 따라서 화살표함수는 내부의 this키워드 값을 변화시키고 싶지 않을 때 사용한다.

<br />

### Lifecycle method

#### Mount
컴포넌트의 인스턴스가 생성되어 DOM 상에 삽입될 때 순서대로 호출된다. component가 마운트될 때, constructor를 호출하고, 그리고 나서 render가 호출된다. 그리고 마지막으로 componentDidMount가 호출된다.

```jsx
class App extends React.Component {
  constructor() {
    super(); // 1번째로 실행
  }

  componentDidMount() {
    console.log('컴포넌트가 마운트 됐을 때 실행') // 3번째로 실행
  }

  render() {
    return ...// 2번째로 실행
  }
}
```

<br />

#### Update
props나 state가 변경되면 업데이트가 되면서 component가 다시 렌더링될 때 순서대로 호출된다.

```jsx
class App extends React.Component {
  constructor() {
    super(); // 1번째로 실행
  }

  componentDidUpdate() {
    console.log('컴포넌트가 업데이트 됐을 때 실행') // 3번째로 실행
  }

  render() {
    return ...// 2번째로 실행
  }
}
```
<br />

#### Unmount
component가 DOM 상에서 제거될 때에 호출된다.

```jsx
class App extends React.Component {
  constructor() {
    super(); // 1번째로 실행
  }

  componentWillUnmount() {
    console.log('컴포넌트가 언마운트 됐을 때 실행') // 3번째로 실행
  }

  render() {
    return ...// 2번째로 실행
  }
}
```

<br />


### 결론 - 신문법을 사용하자
리액트의 공식문서에서도 컴포넌트를 만들 때 function문법으로 사용하라고 권장한다. 복잡한 class 문법이나 this 키워드를 사용하지 않아도 되니 세부 문법을 체크할 필요없이 쉽고 빠르게 리액트 웹개발이 가능해지기 때문이다.

> 둘의 기능 차이는 별로 없지만, useState와 같은 Hook을 자주 사용한다면 function이 더 유용하고, class 컴포넌트는 Lifecycle Hook을 조금 더 자세히 쓸 수 있다.

<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)
- [React 공식 사이트](https://ko.reactjs.org/docs/react-component.html#componentdidmount)