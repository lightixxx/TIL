# CSSTransition

react에 애니메이션을 넣는 방법은 CSS파일에 애니메이션을 제작하고, 컴포넌트가 mount/unmount 될 때 className을 부착하면 된다. `className={}` 중괄호 안에 삼항 연산자를 넣으면 된다.

위 방법 말고, react-transition-group 라는 라이브러리를 설치하고 패턴만 알면 간단한 애니메이션을 부여하기 쉽다.

<br />

## install

```shell
npm install react-transition-group
```
```shell
yarn add react-transition-group
```
```jsx
import { CSSTransition } from react-transition-group;
```
설치를 하고, import하면 사용할 준비는 끝났다.

<br />

## 기본 사용법


### 1. `<CSSTransition></CSSTransition>`으로 애니메이션을 적용할 HTML을 감싸준다.

<br/>

### 2. `<CSSTransition>`에 속성으로 in, classNames, timeout 속성을 넣는다.
className이 아니라 classNames 이다!

```jsx
function App(){
  return (
    <div>
      <CSSTransition in={true} classNames="tabMenu" timeout={500}>
        <TabContent tabMenu={tabMenu} />
      </CSSTransition>
    </div>
  )
}
```
예를 들어 탭메뉴를 만든다고 가정하고 감싸준 뒤, 속성도 넣어줬다.
- in 속성은 일종의 스위치로, true일 때 에니메이션을 적용시켜준다.
- classNames는 어떤 애니메이션을 적용할 지 작명하는 부분이다.
- timeout은 애니메이션 작동시간이다.

### 3. 이제 App.css에 가서 애니메이션을 만들어주면 된다.
```css
.tabMenu-enter {
  opacity : 0
}

.tabMenu-enter-active {
  opacity : 1;
  transition : all 500ms;
}
```
tabMenu 라는 애니메이션의 작동방식을 정의내리면 된다. 
- `.작명-enter` 라는 클래스명은 컴포넌트가 마운트될 때 적용할 CSS
- `.작명-enter-active` 라는 클래스명은 컴포넌트가 등장 중 일때 적용할 CSS 이다.

### 4. in={true}를 평소엔 false였다가 원할 때 true로 바꿔주면 된다.
스위치 상태를 state로 만드는 것이 좋다.

```jsx
function App(){
  
  const [switch, setSwitch] = useState(false);
  return (
    <div>
      <CSSTransition in={switch} classNames="tabMenu" timeout={500}>
        <TabContent tabMenu={tabMenu} />
      </CSSTransition>
    </div>
  )
}
```
false에서 true로 변할 때 애니메이션이 동작한다.
```jsx
function App(){
  
  const [switch, setSwitch] = useState(false);

  return (
    <div>
      <Nav variant="tabs" defaultActiveKey="link-0">
        <Nav.Item>
          <Nav.Link eventKey="link-0" onClick={()=>{ setSwitch(false)}}>Active</Nav.Link>
        </Nav.Item>
        <Nav.Item>
          <Nav.Link eventKey="link-1" onClick={()=>{ setSwitch(false)}}>Option 2</Nav.Link>
        </Nav.Item>
      </Nav>

      <CSSTransition in={switch} classNames="tabMenu" timeout={500}>
        <TabContent tabMenu={tabMenu} />
      </CSSTransition>
    </div>
  )
}

function TabContent(props) {
  useEffect( () => {
    props.setSwitch(true); // 탭 내용 컴포넌트가 로드될 때 true로 변경
  });

  return (
    ...
  )
}
```
1. tab 버튼을 누르면 스위치가 false로 바뀌게 했다.
2. 컴포넌트가 로드될 때 스위치가 true로 바뀌게 했다.(useEffect)


<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)