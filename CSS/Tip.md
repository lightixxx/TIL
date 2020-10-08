# 실무에서 유용한 CSS Tip <i>!</i>


## Image
💡 &nbsp; `<img>` 태그의 width와 height 사이즈를 조절할 때, display를 block으로 바꿔주면 미세한 여백같은 공간이 사라진다 !

<br />

## Inline-block
💡 &nbsp; display 값이 inline-block인 요소는 마크업할 때 생기는 줄바꿈에 의해 알 수 없는 공간이 생긴다 !


<br />

## Margin
💡 &nbsp; `margin` 속성을 사용해서 위아래 간격을 조절할 때는 `margin-top`과 `margin-bottom` 중 한 개만 쭉 사용하는 것이 좋다 ! (얼핏 부모와 자식간에 마진겹침 현상도 영향이 있는 느낌..?)

<br />

## Media Query
💡 &nbsp; 현업에서 모바일과 PC 두 가지 시안이 같이 주어지면 모바일 시안부터 작업하는 것이 편하다!? 특히 가장 작은 사이즈인 아이폰5(width 320px)로 작업을 시작하면 대부분의 디바이스에서 깨지지 않는다.

<br />

## line-height
💡 &nbsp; line-height를 아무리 크게해도 텍스트는 항상 가운데에 위치한다.

<br />

## font-family
💡 &nbsp; body에 font-family를 설정하면 모든 자식에게 적용된다.

<br />

## Typography library 
💡 &nbsp; font-size 의 클래스명은 'fs-'로 시작하기.

💡 &nbsp; font-weight 의 클래스 명은 'fw-'로 시작하기.

💡 &nbsp; color의 클래스 명은 'text-'로 시작하기.

💡 &nbsp; heading 태그와 strong 태그는 default font-weight이 bold이다.

<br />

## sr-only
💡 &nbsp; 시각장애인들은 웹을 스크린리더로 읽기 때문에, 텍스트에 대한 정보를 어느정도 주어야한다. 다만 그 요소가 디자인을 해치거나, 일반인이 봤을 때 굳이 없어도 알 수 있을 정보일때 사용하는 것이 sr-only 클래스이다.
```css
.sr-only {
	position: absolute;
	z-index: -99999;
	width: 1px;
	height: 1px;
	overflow: hidden;
	opacity: 0;
}
```
`position: absolute; z-index: -99999;` 두 가지로도 충분하지만, 더욱 완벽하게 사라지게 만들고 싶을 경우에 width와 height를 1px로 만들고 overflow를 hidden으로 주고 투명도도 0으로 주면 ⭐️완벽⭐️

<br />

## Hover interaction
💡 &nbsp; 링크나 버튼 요소에 interaction을 적용할 때는 보통 250ms로 한다.

<br />

## Width
💡 &nbsp; `width: 0;` 일 때는 어떤 단위도 붙이지 않는 것이 관례이다.

<br />

## Button
💡 &nbsp; 보통 버튼같은 경우 비슷한 스타일이 여러번 사용되는 경우가 많기 때문에 재사용성을 고려한 스타일링과 fill-button과 같은 클래스명을 사용하는 것이 좋다.