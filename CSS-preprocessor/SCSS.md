# SCSS
CSS에 프로그래밍적 요소를 가미한 CSS 전처리기 중 가장 많이 사용되는 녀석이다.

<br />

## 변수
SCSS에서 변수선언은 `$`를 붙여준다. 값으로는 css에서 value로 사용되는 모든 값을 넣을 수 있다.
```scss
$lightix: 1;

p {
  line-height: $lightix;
}
```
위 코드는 컴파일러를 통해
```css
p {
  line-height: 1;
}
```
로 변환되어 사용된다.


### 변수 이름을 지을 때 유의사항
1. 알파벳, -, _, 숫자만 사용할 수 있다. (단, 숫자로 시작할 수는 없다.)
2. 대소문자를 구분한다.

#### 주로 사용되는 코드 컨벤션
1. 소문자만 혹은 대문자만 사용한다.
2. 소문자엔 -숫자를, 대문자엔 _숫자를 붙이는 경향이 있다.

```scss
$lightix-1: 1;
$LIGHTIX_2: 2;
```

### 변수의 scope
```scss
$lightix: 1;

p {
  line-height: $lightix;
}

a {
  $lightix: 2;
  line-height: $lightix;
}
```
SCSS의 코드는 항상 위에서 아래로 읽힌다. 

p태그는 먼저 p태그가 선언된 곳에 `$lightix`변수가 있는지를 확인하고, 없다면 자기 위에 `$lightix`라는 변수가 있는지를 확인하고, 있다면 가장 가까운 값을 가져오게 된다. 



### Design system을 확인하며 변수 선언

<br />

## 주석
SCSS는 두 가지 스타일의 주석을 사용한다
```scss
// 컴파일되지 않는 주석
/* 컴파일되는 주석 */
```

Sass는 컴파일되는 여러줄 주석을 사용할 땐 각 줄 앞에 `*`을 줄맞춰서 붙여야하지만, SCSS는 각 줄에 `*`이 없어도 문제가 없다.

<br />

## 중첩
CSS의 상위 선택자의 반복을 피하고 편리하게 복잡한 구조를 작성할 수 있다.
```scss
.container {
  width: 100%;
  margin: 0 auto;
  .row {
    display: flex;
    flex-wrap: wrap;
  }
}
```

중첩 안에서 `&`키워드는 상위 선택자를 참조해서 치환한다. (원샷 멀티킬 가능)

```scss
button,
input,
select,
textarea {
  background-color: transparent;
  border: 0;

  &:focus {
    outline: none;
    box-shadow: none;
  }
}
```

또한 동일한 네임 스페이스를 갖는 속성들을 다음과 같이 사용할 수 있다.
```scss
html {
  font: {
    weight: bold;
    size: 10px;
    family: sans-serif;
  };
  margin: {
    top: 10px;
    left: 20px;
  };
  padding: {
    bottom: 40px;
    right: 30px;
  };
}
```

## `#{}` 문자 보간
`#{}`을 사용하면 변수 값을 넣을 수 있다.
```scss
$lightixxx: lightixxx;
@import url('http://https://github.com/#{lightixxx}');
```

#### CSS tip!
css 속성선택자 중 동일한 클래스명으로 시작하는 요소를 찾을 땐
`[class^="class 시작명"]`을 적어주면 된다.
```css
[class^="col-"] {
  padding: 0 10px;
}
```

<br />

## 재사용의 끝판왕 @mixin - @include
@mixin을 사용하면 반복되는 코드들 (flex, mediaquery 등)을 편리하게 작성할 수 있다.

@mixin의 작명법은 변수명 짓는 것과 동일하다. 중괄호 안에는 늘 써오던 css 코드를 작성하면 된다.
```scss
@mixin lightix() {
  color: red;
}

p {
  // 넣을 인자값이 없을 경우엔 괄호를 생략해도 된다.
  @include lightix;
}
```


자바스크립트의 함수랑 비슷하게 인자로 값을 넘겨줄 수 있다.
```scss
@mixin lightix($color) {
  color: $color;
}

p {
  @include lightix(blue);
}
```

만약 위 상황에서 $color값을 넣지 않으면 에러가 난다. 하지만, 매번 필요한 것이 아니라, 가끔 필요한 경우에는 기본값으로 $color: false를 적어주면 된다.

```scss
@mixin lightix($color: false) {
  color: $color;
}

p {
  @include lightix;
}
```
하지만 위 경우에 $color값을 넣지 않고 컴파일 해보면, 
```css
p {
  color: false;
}
```
color 값이 false가 된다. 이를 해결하기 위해 조건문을 사용해보자.
```scss
@mixin lightix($color: false) {
  @if (color != false) {
    color: $color;
  }
}
```
이렇게 조건문을 사용해서 분기 처리할 수 있겠지만, 위 코드도 그리 좋은 코드는 아니다. $color 값에 숫자를 넣거나, 아무 값을 넣게되면 false는 아니기 때문에 $color 값에 해당 값이 들어가기 때문이다.

이때 Sass에서 제공하는 type-of()함수를 사용해서 받은 인자값이 맞는 속성인지 체크하면 된다.

```scss
@mixin lightix($color: false) {
  @if (type-of($color) == color) {
    color: $color;
  }
}
```
이런 검사를 유효성 검사, validation check라고 한다. 

<br />

##### 출처
- [HEROPY](https://heropy.blog/2018/01/31/sass)
- [kimbug](https://edu.goorm.io/lecture/25681/%EA%B9%80%EB%B2%84%EA%B7%B8%EC%9D%98-ui-%EA%B0%9C%EB%B0%9C-%EB%B6%80%ED%8A%B8%EC%BA%A0%ED%94%84-%EA%B2%BD%EB%A0%A5%EA%B0%99%EC%9D%80-%EC%8B%A0%EC%9E%85%EC%9C%BC%EB%A1%9C-%EB%A0%88%EB%B2%A8%EC%97%85?utm_source=inhouse_edu_p&utm_medium=display&utm_campaign=kimbug_ui&utm_content=banner)