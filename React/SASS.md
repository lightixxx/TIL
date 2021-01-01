# SASS
CSS 코드의 재활용성을 높여주고, 코드의 가독성을 높여줘서 유지보수를 쉽게 도와주는 pre-processor이다. CSS를 조금 더 프로그래밍 언어답게 변수, 함수, 반복문, 연산자 등을 사용해서 편하게 CSS를 작성하고, 작성한 뒤 CSS로 컴파일하면 된다.

<br />

## install
```bash
yarn add node-sass
```
```bash
npm install node-sass
```
node-sass는 SASS 문법으로 작성된 스타일을 CSS로 컴파일해주는 라이브러리이다.

<br />

## 파일 생성 및 불러오기
```jsx
import './Detail.css'; // CSS 파일 불러오기
import './Detail.scss'; // SCSS 파일 불러오기
```
scss 파일 내에선 SASS 문법을 작성하면 node-sass가 알아서 css로 컴파일 해준다.

<br />

## SASS 문법

### 1. 변수
```scss
$mainColor: #0066ff;

.main-button {
  color: $mainColor;
}
```
`$변수명: 할당할 값;` 이렇게 변수를 만들고, 원하는 곳에서 변수명을 사용한다. 색상 뿐만 아니라 대부분의 모든 값을 넣을 수 있다.

<br />

### 2. @import
CSS 파일 간 import를 할 수 있는 문법이다.
```scss
@import './reset.css';
```
보통은 reset.css 를 저장해두고 `@import`해서 사용한다.

<br />

### 3. nesting
CSS를 작성하다 보면 셀렉터가 너무 길어져서 복잡해지는 경우가 있다.
```css
div.container h4 {
  color: #0066ff;
}

div.container p {
  color: #2860e1;
}
```
scss 파일에선 긴 셀렉터 대신 셀렉터 안에 다른 셀렉터를 넣어서 스타일링을 할 수도 있다.
```scss
div.container {
  h4 {
    color: #0066ff;
  }
  p {
    color: #2860e1;
  }
}
```
셀렉터를 옆으로 길게 나열하는 것이 아니라 안쪽에 중첩해서 작성할 수 있다. 이렇게 사용하면 셀렉터의 해석이 쉽고, 관련된 class끼리 모아서 관리하기 용이하기 때문이다.

<br />

### 4. extend
모든 스타일이 똑같은데 color만 다른 UI가 있을 때, extends 문법을 사용하면 어떤 클래스명에 있던 속성들을 모두 복사할 수 있다.
```scss
.fill-button {
  width: 140px;
  height: 48px;
  border: none;
  border-radius: 2px;
  color: #fff;
  background-color: #3040C4;
  font-size: 15px;
}
.fill-button-inverted {
  @extend .fill-button;
  background-color: #fff;
  color: #3040C4;
}
```
`@extend 클래스명` 을 사용하면 클래스명에 들어있던 모든 내용을 복사해주기 때문에 CSS코드를 재사용하기 매우 편해진다.

<br />

### 5. @mixin / @include
SASS에선 함수도 만들 수 있는데, 선언할 때는 function 키워드 대신 `@mixin`을 사용하고, 호출할 때는 `@include`를 사용한다.
```scss
@mixin makeBtn() {
  width: 140px;
  height: 48px;
  border: none;
  border-radius: 2px;
  color: #fff;
  background-color: #3040C4;
  font-size: 15px;
}

.fill-button {
  @include makeBtn();
}
```
자바스크립트 문법과는 다르게 함수가 위에 선언되어 있어야 밑에서 사용 가능하고, 파라미터도 넣을 수 있다.


<br />
<br />
<br />

##### 출처

- [코딩애플](https://online.codingapple.com)
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)