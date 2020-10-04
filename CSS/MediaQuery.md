# Media Query

화면 해상도에 따라 가로폭이나 배치를 변경하여 데스크탑, 태블릿, 모바일 등 다양한 디바이스의 화면 해상도에서 최적화된 웹사이트를 제공하는 것이 반응형 웹디자인이다. 

<br />

## viewport
```html
<!DOCTYPE html>
<html>
  <head>
    <meta name="viewport" content="width=device-width" />
    ...
  </head>
</html>
```
가장 일반적인 viewport 설정으로 가로폭을 디바이스의 가로폭에 맞추는 것을 의미한다.

<br />

## @media
```css
@media screen and (min-width: 576px) {
  /* 가로폭이 576px이상일 때 적용되는 CSS 작성 */
}
```
디바이스의 크기에 따라 각각의 스타일을 지정하는 것을 가능케 한다.