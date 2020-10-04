# Background

## background-color
배경의 색상을 설정하고 싶을 때 사용하는 속성이다.

```css
.box {
  width: 100px;
  height: 100px;
  background-color: #0066FF;
}
```

### background-color을 설정하는 방법
1. hex (16진 색상 코드)
2. rgb (red, green, blue)
3. rgba (red, green, blue, opacity)

<br />

## background-image
배경의 이미지를 설정하고 싶을 때 사용하는 속성이다. 반드시 url 함수에 이미지가 있는 경로를 작성해서 사용해야 한다.
```css
.box {
  width: 100px;
  height: 100px;
  background-image: url('./assets/image.png');
  /* image를 직접 제공하는 경우 
  현재 css 파일 기준으로 이미지 경로를 작성한다. */
}
```
1. image를 직접 제공하는 경우
     - 현재 css 파일을 기준으로 이미지 경로를 작성한다.

2. 다른 서버나 웹사이트에서 불러오는 경우
   - 해당 이미지가 있는 링크를 작성한다.

<br />

## background-repeat
기본적으로 background-image를 사용할 때, default 값으로 이미지가 반복된다. 반복을 원하지 않을 경우 `background-repeat: no-repeat;`을 지정하면 된다.

<br />

## background-size
background-image를 사용할 경우 그 이미지의 사이즈를 몇으로 할 것인지 설정하는 속성이다. 

1. contain
     - background-image로 설정한 이미지의 모든 면이 잘리지 않고 들어가도록 설정된다.

2. cover
      - background-image로 설정한 이미지가 잘리더라도 빈 공간을 남기지 않고 모두 덮는다.

3. custom
      - %, px, auto 등 원하는 사이즈로 작성할 수 있다. width, height 순으로 작성한다.

<br />

## background-position
x축, y축 순서로 background-image의 위치를 지정할 수 있다.
left, right, center, top, bottom, px, % 등 원하는 위치에 background-image를 설정할 수 있다.