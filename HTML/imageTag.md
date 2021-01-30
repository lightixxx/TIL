# 이미지를 삽입해주는 태그

이미지를 넣어줄 때에는 `<img />`태그를 사용한다
```html
<img src="경로" alt="대체 텍스트" />
```

<br />

### src(source) - 이미지의 파일 경로 지정(필수) 

html 문서에서 이미지 파일까지 찾아가기 위한 경로를 지정해야한다.

```html
<!-- 절대 경로 -->
<img src="https://github.com/lightixxx/profile.jpg" alt="라이틱스의 html 공부" />

<!-- 상대 경로 -->
<img src="../images/html.jpg" alt="라이틱스의 html 공부" />
```

<br />

### alt(alternative text) - 이미지를 설명해주는 대체 텍스트(필수)

이미지가 불러들여지지 않을 때, 이미지를 설명해주는 대체 텍스트이다. 혹은 시각 장에인을 위한 화면 리더기가 이미지에 대한 설명을 할 수 있도록 반드시 입력해야한다.

<br />

### title - 툴팁 표시하기
`<a>`태그와 마찬가지로 마우스 호버시 툴팁이 노출되게 할 수 있다.

<br />

### srcset - 다른 환경에서 사용될 이미지 소스 명시
```html
<img srcset="../images/image1.jpg 1x, ../images/image2.jpg 2x" alt="예시 이미지"/>
```

<br />

### width - 이미지의 가로 너비

### height - 이미지의 세로 너비