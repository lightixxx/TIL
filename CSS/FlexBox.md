# FlexBox

📌 &nbsp; 정렬의 끝판왕 FlexBox를 사용하기 위한 준비 과정 3단계
1. flexbox를 사용할 것이라고 선언!
2. 가로로 정렬할 것인지, 세로로 정렬할 것인지 정하기!
3. 무조건 한 줄 안에 다 정렬시킬 것인지, 상황에 따라 달라질 것인지 정하기!

<br />

## 1. flexbox를 사용할 것이라고 선언!
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

## 2. 가로로 정렬할 것인가, 세로로 정렬할 것인가 !?
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

## 3. 무조건 한 줄에 때려박을지, 눈치보고 달라질지
```css
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  /* nowrap | wrap */
}
```
`flex-wrap`은 자식을 감쌀지 말지를 정하는 프로퍼티이다. 기본값은 `nowrap`으로 감싸지 않고, 자식요소의 사이즈를 줄여서라도 한 줄로 정렬하게 된다. `wrap`을 주면, 한 줄에 모두 정렬하기에 공간이 넉넉하지 않더라도 여러 줄을 만들어서 자식요소를 배치하게 된다.

<br />

