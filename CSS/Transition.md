# Transition
가령 클래스가 붙거나, 마우스를 올리는 등 사용자가 어떤 행위를 했을 때, 요소의 변화가 바로 바뀌는 것이 아니라 '스르륵~' 변하게 할 때 사용한다.

```css
.box {
  transition: property duration [timing-function] [delay];
}
```

## property (필수)
어떤 속성에 transition이 일어나게 할 것인지 설정한다. 익히 알고있는 css property를 작성하면 된다. 모든 속성에 transition을 걸고 싶을 때는 `all` 키워드를 넣으면 된다.
```css
.box {
  transition: font-size;
  /* css properties | all */
}
```

<br />

## duration (필수)
transition이 얼마동안 일어날 것인지 즉, 지속 시간을 설정하는 속성이다. 단위는 ms와 s로 시간을 명시할 수 있다.

```css
.box {
  transition: font-size 2000ms;
  /* s | ms */
}
```

<br />

## timing-function (선택)
transition이 일어날 때, 변화의 속도를 지정할 수 있는 속성이다.
```css
.box {
  transition: font-size 2000ms ease-in;
  /* ease-in | ease-out | ease-in-out | cubic-bezier() 등 */
}
```
### 자주 사용하는 timing-function
1. ease-in : 점점 빠르게
2. ease-out : 점점 느리게
3. ease-in-out : 1,2번 짬뽕
4. cubic-bezier() : 가속도를 직접 조절하고 싶을 때 사용(cubic-bezier.com 에서 조절해서 복붙!)

<br />

## delay (선택)
transition이 어느정도 지연됐다가 일어났으면 싶을 때 사용하는 속성이다.
```css
.box {
  transition: font-size 2000ms ease-in 1000ms;
  /* s | ms */
}
```