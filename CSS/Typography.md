# Typography

디자인에 있어서 활자의 서체나 글자 배치 등의 구성 및 표현을 말한다.

웹은 곧 정보를 공유하는 매개체이며, 그 정보를 구성하는 대다수는 텍스트로 이루어져있다. 따라서 텍스트가 어떻게 배치되어 있는지에 따라 가독성이 달라지고, 가독성이 좋으면 사용자 경험(UX)도 좋아지기 때문에 잘 알아두는 것이 좋다!

<br />

## font-size
글자의 크기를 설정할 때 사용하는 속성이다.

```css
.box {
  font-size: 16px;
}
```

font-size를 설정할 때 사용할 수 있는 단위
1. px: 절대 단위 
2. em: 상대 단위
    - Equal to capital M
    - 대문자 M사이즈의 크기를 기준으로 한다.
    - 실제로 적용된 font-size 를 1em으로 한다.
    - 불안정하기 때문에 잘 사용하지 않는다.

3. rem: 상대 단위
    - Root EM
    - HTML에 적용된 font-size를 1rem으로 한다.

<br />

## line-height
줄의 높이 즉, 줄간격을 설정할 때 사용하는 속성이다.
```css
.box {
  line-height: 1.5;
}
```
줄간격은 주로 적용된 폰트사이즈에 비례해서 적용하는 것이 편하기 때문에 **em**을 많이 사용한다. px과 rem은 단위를 작성해야 하지만, em은 생략하는 것이 관례이다.

<br />

## letter-spacing
글자와 글자 사이의 간격 즉, 자간을 설정할 때 사용하는 속성이다.

```css
.box {
  letter-spacing: -.03em;
}
```
자간도 line-height와 마찬가지로 폰트 사이즈에 비례해서 적용하는 것이 좋은 관례이기 때문에 **em**을 사용한다. 하지만 line-height와는 다르게 단위를 생략하면 안된다.

<br />

## font-famliy
폰트 서체를 설정할 때 사용하는 속성이다.
```css
.box {
  font-family: "Poppins", "Roboto", sans-serif;
}
```
font-family 값으로 적힌 순서대로 적용이 되며, 첫 번째로 작성된 서체가 없을 경우 두 번째 서체(fallback font)가 적용된다.

<br />

## font-weight
폰트의 무게 즉, 폰트의 굵기를 설정할 때 사용하는 속성이다.
```css
.box {
  font-weight: 400;
  /* 100 ~ 900 까지 100단위로 이루어져 있다. */
}
```

- 100 : thin
- 300 : light
- **400 : regular**
- 500 : medium
- **700 : bold**
- 900 : black

<br />

## color
글자의 색상을 설정할 때 사용하는 속성이다.
```css
.box {
  color: #ff4949;
}
```

color을 설정하는 방법
1. hex (16진 색상 코드)
2. rgb (red, green, blue)
3. rgba (red, green, blue, opacity)

<br />

## text-align
글자의 정렬 방법을 설정할 때 사용하는 속성이다.
```css
.box {
  text-align: center;
}
```

text-align을 설정하는 방법
1. left: 왼쪽 정렬
2. center: 가운데 정렬
3. right: 오른쪽 정렬

<br />

## text-indent
들여쓰기할 때 사용하는 속성이다.
```css
.box {
  text-indent: 100px;
  /* 음수도 가능 */
}
```

<br />

## text-transform
텍스트의 변형을 일으킬 때 사용하는 속성이다. 한글에는 소용이 없고, 영어에 주로 사용한다.
```css
.box {
  text-transform: uppercase;
  /* none | capitalize | uppercase | lowercase */
}
```

1. none : 마크업한 텍스트에서 변형이 일어나지 않는다.
2. capitalize : 단어의 첫 글자가 대문자로 변한다.
3. uppercase : 모든 글자가 대문자로 변한다.
4. lowercase : 모든 글자가 소문자로 변한다.

<br />

## text-decoration
텍스트를 꾸미는 방법을 설정할 때 사용하는 속성인데, 주로 줄을 긋는데 사용한다. a 태그의 경우 기본 text-decoration이 underline 이기 때문에 해제할 때 사용한다.
```css
.box {
  text-decoration: underline;
  /* none | underline | line-through | overline */
}
```
1. none : 자동으로 생기는 밑줄을 없앨 때 사용한다.
2. underline : 밑줄을 긋는다.
3. line-through : 텍스트 중간에 줄을 긋는다.
4. overline : 윗줄을 긋는다.

<br />

## font-style
폰트의 스타일을 설정할 때 사용하는 속성인데, 주로 italic 만 사용한다. `<em>` 태그의 경우 기본 font-style이 italic이기 때문에 해제할 때 사용한다.
```css
.box {
  font-style: italic;
  /* normal | italic | oblique */
}
```
1. normal: 기본 값
2. italic : 기울임
3. oblique : 기울임 ?

