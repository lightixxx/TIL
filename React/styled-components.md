# styled-components
JS 안에 CSS를 작성하는 것 중 가장 인기 있는 라이브러리이다.

컴포넌트가 많아질수록 스타일링할 때 불편함이 생긴다.
1. class로 만든 것을 잊고 중복해서 또 만든다.
2. 다른 컴포넌트에 원하지 않는 스타일이 적용된다.
3. CSS 파일이 너무 길어진다.

이런 불편함을 해결하기 위해 컴포넌트 제작할 때 스타일을 바로 입힐 수 있는데, 그때 유용한 라이브러리가 styled-components 이다.

<br />

## install
```shell
yarn add styled-components
```
```shell
npm install styled-components
```
설치를 하고, 사용하고 싶은 컴포넌트에 import 한다.
```jsx
import styled from 'styled-components';
```

<br />

## 사용법
styled-components를 이용하면 컴포넌트를 만들 때 스타일을 미리 만들 수 있다. 예를 들어 `padding: 20px`인 `<div>`를 styled-components를 이용해서 만든다고 가정해보자.
```jsx
import styled from 'styled-components';

let 박스 = styled.div`
  padding : 20px;
`;

function Detail(){
  return (
    <div>
      ...
      <박스>나는 패딩 20px 박스!</박스>
    </div>
  )
}
```
`<div>` 박스를 만들고 싶으면 `styled.div`를, `<h2>` 제목을 만들고 싶으면 `styled.h2`를 쓰면 된다. 그 뒤에 백틱을 이용해서 기본 스타일을 css 작성하듯 쓰면 된다. 그리고 그것을 변수로 저장하면 컴포넌트가 된다.

따로 CSS 파일을 건들일 필요가 없고, class 선언 없이 컴포넌트를 만들 수 있다는 장점때문에 사용한다.

<br />

## props로 스타일링
props 문법을 이용해서 비슷한 UI에 필요한 부분의 스타일만 수정해서 사용하는 방법이다.

```jsx
import styled from 'styled-components';

let 제목 = styled.h4`
  font-size : 25px;
  color : ${ props => props.색상 };
`;

function Detail(){
  return (
    <div>
      ...
      <제목 색상="blue">안녕하세요!</제목>
      <제목 색상={'red'}>안녕하세요!</제목>
    </div>
  )
}
```
제목 이라는 변수에 `font-size`와 `color`를 지정하고, 색상 입력란에 `${}` 를 통해 문자 중간에 함수나 변수를 넣을 수 있도록 했다. 그리고 `props.색상`이라는 props 변수를 넣어서 props로 원하는 문자를 전송할 수 있게 됐다. 즉, 같은 컴포넌트인데 props 문법을 통해 각각 다른 스타일을 넣을 수 있다는 것이다.

> react에서 props를 전송하는 두 가지 방법
> 1. 일반 텍스트를 전달하고 싶을 땐, "" 따옴표를 사용한다.
> 2. 변수나 자료형을 담고 싶을 땐, {} 중괄호를 사용한다.

<br />

### 결론
styled-components를 배웠지만 사용할지는 의문이다. 
~~(회사에서 쓰라면 써야겠지만)~~
그냥 css를 Import 하는게 더 편하기도 하고.. js파일에서 스타일 관리하면 나중에 더 복잡해질 것 같아서..

다만 장점을 찾아보자면
1. 스타일을 넣을 때 다른 파일이랑 컴포넌트 명이 겹쳐도 CSS 적으로 문제가 생기지 않는다는 것
2. 컴포넌트 스타일 수정을 할 때 컴포넌트 안에서 찾으면 된다는 것
정도..





<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)