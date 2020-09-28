# Position
레이아웃 구성할 때, 내가 원하는 위치로 요소를 이동시키기 위해 사용하는 속성으로 static, relative, absoulte, fixed, sticky 가 있다.

📌 position 속성을 준 요소의 기준점이 무엇인지 생각하면서 구성해야 한다.

<br />

## Static (기본 위치)
모든 요소의 기본 position 값이다. 일반적인 상태를 말한다. 좌표 프로퍼티를 같이 사용할 수 없고, 사용할 경우엔 무시된다.

<br />

## Relative (상대)
float와 마찬가지로 붕 뜨는 것은 맞지만, 자신이 원래 있던 위치를 기억하고 있어서 다른 요소에 영향을 주지 않고, 레이아웃이 무너지지 않는다. 기준점에서 부터 좌표 프로퍼티를 사용해 위치시킬 수 있다.

📌 기준점 : 자기 자신이 본래에 있던 자리를 기준으로 한다.

<br />

## Absoulte (절대)
float와 마찬가지로 부모가 높이를 알지 못하고, `display: block;`이 되지만, 길막은 하지 못한다. layer가 하나 붕 띄워지는 것과 같은 개념.

📌 기준점 : 자신을 감싸고 있는 부모요소 중, `position: static;`이 아닌 부모를 기준으로 한다.

<br />

## Fixed (고정)
absoulte 와 같은 효과를 준다. 하지만, viewport 사이즈에 맞춰 스크롤이 되더라도 사라지지 않고 항상 그 위치에 고정되어있다.

📌 기준점 : viewport 사이즈를 기준으로 한다.

<br />

## Top, Bottom, Left, Right
좌표 프로퍼티

⭐️ Top과 Bottom 중 하나, Left와 Right 중 하나(해당 위치와 가까운 쪽)를 사용하는 것이 좋다.

<br />

## Z-index
position을 사용하면 붕 띄우는 것은 같다. z-index에 큰 정수 값을 지정할 수록 화면 전면에 출력된다.