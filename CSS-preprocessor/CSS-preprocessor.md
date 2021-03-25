# CSS preprocessor (CSS 전처리기)
프로젝트의 규모가 커질수록 모든 style을 CSS로 처리하기엔 불편함이 많다. 불필요한 선택자를 남발하게 되고, 연산처리가 되지 않기 때문이다. 때문에 나온 것이 CSS 전처리기 이다. CSS가 동작하기 전에 사용하는 기능으로, CSS에 프로그래밍적 요소를 가미한 녀석이라고 생각하면 된다.


그리드 시스템을 작성한다고 했을 때,
```css
.col-1 {
  width: 105px;
}

.col-2 {
  width: 210px;
}

.col-3 {
  width: 315px;
}
...
```
css에서는 이렇게 하나하나 작성을 해줘야한다.

```scss
$columns: 12;
$gutter: 30px;
$unit: 75px;

@for $i from 1 through 12 {
  .col-#{$i} {
    width: $i * ($unit + $gutter);
  }
}
```
반면 SCSS에서는 연산과 반복 등 이 가능해져서 간결하게 작성할 수 있다.

다만 웹에서 직접 동작하지 않기 때문에 웹에서 동작 가능한 CSS로 컴파일을 해서 사용한다.

<br />

## Sass(Syntactically awesome stylesheet)
Sass의 3버전에서 새로 등장한 SCSS는 CSS 구문과 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합이다.

간단한 차이로는 `{}`중괄호와 `;`세미콜론의 유무이다.

```SCSS
// Sass
.list
  width: 100px
  float: left
  li
    color: red
    &:last-child
      margin-right: 10px
```

```SCSS
// SCSS
.list {
  width: 100px;
  float: left;
  li {
    color: red;
    &:last-child {
      margin-right: 10px;
    }
  }
}
```
Sass는 선택자의 유효범위를 '들여쓰기'로 구분하고, SCSS는 `{}`중괄호로 구분한다.

<br />

## node-sass
Sass(SCSS)는 웹에서 직접 동작할 수 없기 때문에 node-sass를 통해 CSS로 컴파일을 해야한다.

NPM으로 전역 설치해서 사용한다.
```bash
npm install -g node-sass
```

컴파일 하려는 파일의 경로와 컴파일된 파일이 저장될 경로를 설정한다.

```bash
node-sass [옵션] <입력파일경로> [출력파일경로]
node-sass -wr styles/main.scss style.css
```

주로 사용되는 옵션은 -w(--watch), -r(--recursive)이다. 한번에 -wr로 넣어줄 수 있다.
- -watch는 저장하면 실시간으로 변화가 적용된다.
- -recursive는 여러가지 파일의 모든 변화를 인식해 적용된다.

조금 더 편하게 사용하기 위해서는 package.json 파일에 scripts 항목에 넣어서 사용할 수 있다.

```json
"scripts": {
  "test": "...",
  "node-sass": "node-sass",
  "sass": "node-sass -wr styles/main.scss style.css",
}
```

추가로 옵션에 `--source-map true` 를 추가하게 되면, 개발자 도구에서 확인할 때 해당 스타일이 어떤 scss파일 몇 번째 줄에서 실행된 것인지 알 수 있다.