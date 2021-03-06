# useState
사용자의 인터렉션에 따라 바뀌어야 할 때, 동적으로 값이 바뀌는지 구현하기.

리액트의 Hooks라는 기능이 도입되면서 함수형 컴포넌트에서도 상태를 관리할 수 있게 됐다.

<br />

## 중요한 데이터는 변수말고 state에 만들자
1. state는 변수 대신 사용하는 데이터 저장공간이다.
2. `useState()`를 이용해서 만든다.
3. 문자, 숫자, 배열, 객체 모두 저장 가능하다.

`useState('lightix')` 는 `[state 데이터, state 데이터 변경 함수]` 를 리턴하기 때문에 `let [title, change] = useState('lightix')`는 ES6문법인 구조분해할당을 통해 `let title = 'lightix'; let change = lightix의 데이터 변경 함수`가 들어간다.

<br />

### Q. 변수로 저장하면 되는데, 왜 state에 저장하는가?
- Web이 App처럼 동작하게 만들기 위해서이다.
- state에 저장된 데이터가 변경이 되면 HTML이 자동으로 재렌더링이 된다. 

그냥 변수로 저장한 데이터는 변경이 되어도 자동 재렌더링이 안되고 새로고침해야 렌더링 된다. 예를 들어 제목을 정렬하거나, 수정하거나해도 새로고침 없이 페이지를 부드럽게 재렌더링해준다.

<br />
<br />
<br />

##### 출처
- [코딩애플](https://online.codingapple.com/unit/react4-setstate-usestate-onclick-eventhandler/?id=2305)