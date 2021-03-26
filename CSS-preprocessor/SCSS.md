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

