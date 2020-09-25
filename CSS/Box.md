# Box
모든 HTML 요소는 Box로 표현이 된다. 

<br />

## Box Model
요소들을 스타일링하고, 크기를 잡고, 영역을 잡을 때 가장 많이 사용하게 되는 속성이다.

- Content: width, height로 구성되어 있다.
- Padding: 안쪽 여백, 즉 content와 border 사이의 공간을 나타낸다.
- Border: 테두리 영역으로 굵기, 스타일, 색상, 반경 등을 설정할 수 있다.
- Margin: Border 바깥에 위치하는 요소의 외부 여백 영역을 말한다.

<br />

## Box Sizing
`box-sizing` 프로퍼티는 width, height 프로퍼티의 대상 영역을 변경할 수 있다. 

`box-sizing`의 defalut 값은 content-box이다. 즉, width와 height의 영역이 content 영역을 의미한다. `box-sizing: border-box;` 로 설정하면 마진을 제외한 border, padding 영역까지 width와 height의 영역이 되므로 별도의 계산없이 레이아웃을 직관적으로 사용할 수 있게 된다.

<br />

## Box Type (Display)
layout 정의에 자주 사용되는 중요한 프로퍼티이다.
- block level elements
- inline level elements
- inline-block level elements
<br />

### Block

기본적으로 '길막'을 한다. 브라우저가 HTML 문서를 렌더하는 과정에서 마크업이 된 순서대로 위에서 아래로 차곡 차곡 쌓이게 된다. 쌓아 올린 요소가 block box라면 자기 자신 다음에 오는 요소는 옆에 오지 못하게 '길막'을 하게 된다.

- width를 선언하지 않은 경우, width는 부모의 content-box의 100%가 된다.
- 따로 width를 선언한 경우, 남은 공간은 margin으로 채워진다.
- 부모의 height를 선언하지 않은 경우, 자식 요소의 height의 합이 부모의 height가 된다.

<br />

### Inline
기본적으로 컨텐츠를 흐르게 배치하는 '흐름'을 갖는다. 

📍 <nbsp> 인라인 요소는 옆으로 흐르는 속성을 갖기 때문에 흐름을 깨는 아래 속성들은 사용할 수 없다.
- **width**
- **height**
- padding-**top**
- padding-**bottom**
- border-**top**
- border-**bottom**
- margin-**top**
- margin-**bottom** 

padding-top, padding-bottom 은 적용이 되는 듯 보이지만 실제로 영역을 차지하지 않는다.

<br />

### Inline Block

block의 좋은 점과, inline의 좋은 점을 섞은 '사기템' 같은 녀석이다. inline 처럼 흐름에 따라 한 줄에 표현되면서 width, height, margin, padding 을 모두 사용할 수 있다.