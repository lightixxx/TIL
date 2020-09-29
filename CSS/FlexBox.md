# FlexBox

📌 &nbsp; 정렬의 끝판왕 FlexBox를 사용하기 위한 준비 과정
1. flexbox를 사용할 것이라고 선언!
2. 가로로 정렬할 것인지, 세로로 정렬할 것인지 정하기!
3. 무조건 한 줄 안에 다 정렬시킬 것인지, 상황에 따라 달라질 것인지 정하기!

<br />

## 1. flexbox를 사용할 것이라고 선언! (display)
```css
.flexbox {
  display: flex;
  /* flex | inline-flex */
}
```
`display`는 박스의 타입을 정해주는 프로퍼티이고, `flex`도 기본적으로 박스의 타입 중 하나이다. `block`과 유사하지만, 쉽게 정렬할 수 있게 해준다. `inline-flex`는 `inline-block`와 유사하지만, 마찬가지로 쉽게 정렬할 수 있게 해준다.

<br />

### 누구한테 ?
정렬을 하고자하는 요소를 감싸고 있는 부모요소한테 `display: flex;`를 주어야 한다.

<br />

## 2. 가로로 정렬할 것인가, 세로로 정렬할 것인가 !? (flex-direction)
```css
.flexbox {
  display: flex;
  flex-direction: row;
  /* row(가로) | row-reverse(가로축 반대) | column(세로) | column-reverse(세로축 반대) */
}
```
`flex-direction` 프로퍼티를 사용하면 두 개의 축이 생긴다. `flex-direction`의 방향에 따라 Main axis가 생기고, 그것의 수직을 이루는 방향으로 Cross axis가 생긴다. 축이 흐르는 방향은 왼쪽에서 오른쪽으로, 위쪽에서 아래쪽으로 흐른다. 

- `flex-direction: row;`는 main axis가 왼쪽에서 오른쪽으로, cross axis가 위쪽에서 아래쪽으로 흐른다.

- `flex-direction: column;`은 main axis가 위쪽에서 아래쪽으로, cross axis가 왼쪽에서 오른쪽으로 흐른다.

- `flex-direction: row-reverse;`는 main axis가 오른쪽에서 왼쪽으로, cross axis가 위쪽에서 아래쪽으로 흐른다.

- `flex-direction: column-reverse;`은 main axis가 아래쪽에서 위쪽으로, cross axis가 왼쪽에서 오른쪽으로 흐른다.

<br />

## 3. 무조건 한 줄에 때려박을지, 눈치보고 달라질지 (flex-wrap)
```css
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  /* nowrap | wrap | wrap-reverse */
}
```
`flex-wrap`은 자식을 감쌀지 말지를 정하는 프로퍼티이다. 기본값은 `nowrap`으로 감싸지 않고, 자식요소의 사이즈를 줄여서라도 한 줄로 정렬하게 된다. `wrap`을 주면, 한 줄에 모두 정렬하기에 공간이 넉넉하지 않더라도 여러 줄을 만들어서 자식요소를 배치하게 된다.

<br />

## justify-content
`flex-direction`에 따라 생기는 main axis를 기준으로 해서 요소를 정렬해주고 싶다면 `justify-content` 프로퍼티를 사용해서 정렬을 하면 된다.
```css
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  /* flex-start | flex-end | center | space-between | space-around */
}
```
`flex-direction: row;`에서는 main axis가 왼쪽에서 오른쪽으로 흐르기 때문에
- flex-start: 왼쪽 정렬이 된다.
- flex-end: 오른쪽 정렬이 된다.
- center: 가운데 정렬이 된다.
- space-between: 요소들끼리의 사이(between) 간격을 동일하게 나눠갖는다.
- space-around: 요소들 양 옆의 간격을 동일하게 나눠갖는다.

<br />

## align-items
`flex-direction`에 따라 생기는 **하나의 cross axis를 기준으로 요소를 정렬** 해주고 싶다면 `align-items` 프로퍼티를 사용해서 정렬을 하면 된다.
```css
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-items: stretch;
  /* stretch | flex-start | flex-end | center | baseline */
}
```
`flex-direction: row;`에서는 cross axis가 위쪽에서 아래쪽으로 흐르기 때문에
- flex-start: 위쪽 정렬이 된다.
- flex-end: 아래쪽 정렬이 된다.
- center: 가운데 정렬이 된다.
- baseline: baseline(텍스트 아래 줄)을 기준으로 정렬이 된다.

<br />

## align-content
`flex-wrap: wrap`을 사용하면 부모 요소의 크기보다 자식요소 크기의 합이 더 클 경우, 넘쳐지는(?) 자식요소는 다음 줄로 내려가면서 절반을 나눠 새로운 축이 하나 더 생성한다. 이때 각각의 축에 맞춰 정렬을 하고 싶을 땐 `align-items`를 사용하면 되지만, 각각의 축을 무시하고 한 축을 기준으로 정렬하고 싶을 때 사용하는 것이 `align-content`이다.
```css
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: flex-start;
  /* flex-start | flex-end | center | space-between | space-around */
}
```
<br />
- flex-stert: 위쪽 정렬이 된다.
- flex-end: 아래쪽 정렬이 된다.
- center: 가운데 정렬이 된다.
- space-between: 요소들끼리의 사이(between) 간격을 동일하게 나눠갖는다.
- space-around: 요소들 양 옆의 간격을 동일하게 나눠갖는다.

#### 센세의 깨알 tip
뭔가 복잡 미묘하다면 먼저 `align-items` 를 믿고 사용해보고, 원하는 정렬이 아니라면 `align-content`를 사용하자!

<br />

## 자식요소에게 주는 프로퍼티
flex의 영향을 받은 자식요소에게 주는 속성.

<br />

### order
정수 값을 주어 마크업된 순서를 마음대로 바꾼다. 기본값은 0으로 숫자가 클수록 뒤에 배치된다.

<br />

### flex-grow
양의 정수 값을 주어 컨텐츠 너비보다 커질 때 원래 컨텐츠를 제외한 여백을 나눠갖는다. flex-item에 `flex-grow: 5;` 를 주면 다른 flex-item의 5배 너비를 갖는다.

<br />

### flex-basis
flex-item의 너비 기본값을 px, % 등의 단위로 지정해 원래 컨텐츠가 점유하는 비율을 결정한다.

<br />

### flex-shrink
양의 정수 값을 주어 컨텐츠 너비보다 작아질 때 원래 컨텐츠를 제외한 여백을 나눠 갖는다. 기본값은 1이고, 0을 지정하면 축소가 해제되어 원래의 너비를 유지한다.

<br />

### align-self
자식요소 각각 다른 정렬을 원할 때 사용하는 프로퍼티이다. 
```css
.flex-item {
  align-self: auto
  /* auto | flex-start | flex-end | center | baseline | stretch */
}
```

<br />

#### `flex-grow`, `flex-basis`, `flex-shrink` 는 축약형으로 `flex: 1`로 사용할 수 있지만 W3C에서는 개별적으로 기술하는 것을 추천한다.