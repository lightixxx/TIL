# Animation
transition는 단순히 요소의 프로퍼티 변화에 주안점이 있다면, animation은 세부적인 움직임을 시간 흐름에 맞게 제어할 수 있고, 재생 정지 반복까지 제어할 수 있기 때문에 transition보다 제한이 적다. 

<br />

## @keyframes name
애니메이션의 흐름 중 여러 시점에서 각각의 css 속성값을 지정할 수 있다.
```css
/* 처음과 끝의 애니메이션만 지정할 때 */
@keyframes name1 {
  from {
    /* rules */
  }
  to {
    /* rules */
  }
}

/* 세부적으로 애니메이션을 지정할 때 */
@keyframes name2 {
  0% {
    /* rules */
  }
  30% {
    /* rules */
  }
  70% {
    /* rules */
  }
  100% {
    /* rules */
  }
}
```

<br />

## animation-name
@keyframes 애니메이션 이름을 지정한다.
```css
.box {
  animation-name: move;
}
```

<br />

## animation-duration

한 싸이클의 애니메이션에 소요되는 시간을 s 혹은 ms로 지정한다.
```css
.box {
  animation-duration: 1000ms;
}
```
<br />

## animation-timing-function
애니메이션이 변화하는 속도가 어떤 방식으로 진행될지에 대한 속성을 지정한다.
```css
.box {
  animation-timing-function: ease-in;
  /* ease-in | ease-out | ease-in-out | cubic-bezier() */
}
```

<br />

## animation-delay
애니메이션이 시작하는 시간을 s 혹은 ms로 얼마나 딜레이 시킬지 지정한다.
```css
.box {
  animation-delay: 5000ms;
}
```
<br />

## animation-iteration-count
애니메이션의 재생 횟수를 지정한다.
```css
.box {
  animation-iteration-count: 3;
  /* infinite | 정수 */
}
```
<br />

## animation-direction
애니메이션이 종료된 후 반복될 때 진행 방향을 지정한다.
```css
.box {
  animation-direction: alternate;
  /* normal | reverse | alternate | alternate-reverse */
}
```
<br />

