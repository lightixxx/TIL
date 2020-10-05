# Etc

## Box Shadow
그림자를 설정하는 속성으로,
h-offset | v-offset | blur | spread | color 를 작성한다.


#### 1. h-offset
x축으로 얼마나 이동할 것인지 설정한다. 양수이면 오른쪽으로, 음수이면 왼쪽으로 그림자가 생긴다.


#### 2. v-offset
y축으로 얼마나 이동할 것인지 설정한다. 양수이면 아래쪽으로, 음수이면 위쪽으로 그림자가 생긴다.

#### 3. blur
흐린 정도를 설정한다. 0은 흐림정도가 없고, 숫자가 커질 수록 점점 더 흐려진다. 단위는 px을 사용한다.

#### 4. spread (선택)
그림자의 크기를 설정한다. 숫자가 커질 수록 점점 커진다. 단위는 px를 사용한다.

#### 5. color
어떤 색상으로 그림자를 넣을 지 설정한다.

<br />

## Opacity
투명도를 설정할 때 사용한다. 0~1 사이의 값을 입력한다.

<br />

## Overflow
width와 height 값을 가질 수 있는 요소 안에 있는 컨텐츠나 자식 요소가 width와 height를 벗어났을 때 어떻게 처리할 것인가에 관한 속성이다. 

```css
.box {
  overflow: hidden;
  /* visible | auto | scroll | hidden */
}
```

1. visible : default 값으로, 넘쳐 흐르던 말던 그냥 내비둬라!
2. auto : 넘쳐 흘렀을 때, 알아서 하라!
3. scroll : 넘쳐 흘렀을 때, 스크롤로 표시하라! (auto와 비슷..)
4. hidden : 넘쳐 흘렀을 때, 숨겨라!

#### overflow-x | overflow-y 를 따로 설정할 수도 있다.

<br />

## transform
요소를 2차원 혹은 3차원의 공간에서 변형하는 속성이다.


### 1. translate(x,y)
다른 곳으로 움직일 때 사용하는 속성으로 단위는 px, %을 사용할 수 있다. %는 자기 자신의 크기를 기준으로 움직인다. 원래 위치를 기억하기 때문에 다른 요소에 영향을 끼치지 않는다.

`translateX()`와 `translateY()`로 각각 설정할 수도 있다.

<br />

### 2. scale(N)
자기 자신의 크기를 N의 배율만큼 키울 때 사용하는 속성이다. 자기 자신의 크기는 기억을 하고있기 때문에 다른 요소에 영향을 끼치지 않는다.

`scale(x,y)` 로 width와 height의 배율을 각각 지정할 수도 있다.

<br />

### 3. rotate(Ndeg)
각도를 Ndeg 만큼 돌려줄 때 사용하는 속성이다. 다른 요소에 영향을 끼치지 않는다.

<br />

## Visibility
요소를 보여줄 지 말지 설정하는 속성이다. visible과 hidden을 값으로 줄 수 있다. 
```css
.box {
  visibility: hidden;
}
```
`display: none;`은 box의 타입이 없다는 뜻으로 없는 존재 취급하지만, `visibility: hidden;`은 존재는 하지만 보이지 않겠다는 뜻이다.