# DOM (Document Object Model)

DOM은 HTML 문서를 위한 프로그래밍 인터페이스이다. 

여기서 프로그래밍 인터페이스는 여러 소프트웨어 사이에서 교류를 할 수 있게 해주는 도구(?) 같은 것을 말한다. 예를 들어, 리모콘을 통해 TV 화면을 조작하는 것과 비슷하다.

요약하자면 DOM은 HTML문서를 위해 여러 소프트웨어 사이에서 교류를 가능케하는 도구이다. 따라서 DOM을 통해 HTML을 마음대로 조작할 수 있다.

HTML 문서는 브라우저가 화면을 그리기 위한 **초기 설계도의 역할**을 한다. 브라우저는 초기 설계도를 기반으로 화면을 그리게되고, CSS를 통해 화면을 꾸미게 된다. 그리고 그 화면을 DOM으로 접근하고 조작하게 되는 것이다. 

주의할 것은 자바스크립트로 화면을 수정한다고 해서 HTML문서 자체가 수정되는 것은 아니다.

<br />

## 자바스크립트 입장에서 HTML문서는 문자열이다.
문자열로만 보이는 HTML을 DOM을 통해 JavaScript가 이해할 수 있는 Object 형태로 바꾼 것이라고 이해하면 쉽다.
```jsx
const htmlDocumentContent = `
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <div>
      <div>child 1</div>
    </div>
  </body>
  </html>
`
```
단순히 이 문자열을 최소한의 의미가 있는 단위로 쪼개야하기 때문에 child 1을 가져오기 위해서
```jsx
const child1 = {
  nodeType: 1,
  nodeName: 'div',
  childNode: [],
  attribute: [],
}
```
이런 객체형태로 바꿔주는(PARSE) 녀석이 DOM이다.

<br />

## Document Nodes
HTML의 시작이 DOCTYPE이듯 HTML 문서에 대한 정보를 갖고 있는 것이 Document Node이다.

<br />

### 1. document.getElementById('id 명')
아이디는 기본적으로 하나의 HTML에서 고유한 값이어야 하기 때문에, 단 하나의 요소가 선택된다. 

그 하나의 요소는 Node 혹은 HTML Element라고 부르는 것이다. Node가 조금 더 포괄적인 상위 개념이고, HTML Element는 한 단계 하위 개념이다.

<br />

### 2. document.getElementByClassName('class 명')
class는 HTML에서 주로 여러개를 그룹지어 사용하기 때문에 `getElementByClassName()` 함수를 이용해서 선택할 경우 모두 배열과 유사한 형태가 된다. 그리고 그 유사배열에 담긴 배열의 요소들이 하나의 HTML Element이다. 따라서 거의 대부분의 상황에서 배열의 인덱스 위치를 이용해서 사용해야 한다.

<br />

### 3. document.getElemenetByTagName('tag 명')
특정 태그를 사용한 요소들을 선택할 수 있는 함수다. 해당 태그가 여러개라면 `getElementByClassName()`와 마찬가지로 유사배열의 형태로 요소를 가져온다.


<br />

### 4. document.querySelector('CSS 선택자')
CSS 선택자 문법을 이용해서 요소를 선택할 수 있다. ID, Class, tagName 등 간편하게 선택할 수 있기 때문에 가장 많이 사용되는 방법이다.


<br />

## Element Nodes
Element는 HTML 태그와 같은(?) 뜻이다. 즉 HTML 태그는 Element이자 요소이다. 사용자의 행동을 예측해서 정적인 상태인 HTML에 개입해 속성을 바꿀 때 필요한 것이 DOM이다. 이것을 염두하고 공부하면 맥락을 파악하기 쉽다.

- createElement()
- getAttribute()
- setAttribute()
- classList()

### 1. `cretateElement(tagName)`
지정한 `tagName`의 HTML 요소를 만들어서 반환한다.
```js
// h1 요소를 만들어서 heading이라는 변수에 할당
const heading = document.createElement('h1');
```
> 주의할 것은 자바스크립트로 생성한 요소는 직접 화면에 명시적으로 추가하기 전까지 화면에 나타나지 않는다. 즉, 생성만 했을 뿐, 화면에 추가하지는 않은 상태이다.

<br />

### 2. `getAttribute(attributeName)`
해당 요소의 지정된 값을 반환한다. 존재하지 않는 속성이라면 null이나 ""(빈문자열)을 반환한다.
```js
// 해당 요소의 href 값을 attribute라는 변수에 할당
const attribute = elem.getAttribute('href');
```

<br />

### 3. `setAttribute(attributeName, value)`
해당 요소에 속성과 값을 세팅한다.
```js
// 해당 요소에 href 값을 http://www.lightix.com로 세팅
elem.setAttribute('href', 'http://www.lightix.com');

// class 속성을 세팅하게 되면, 기존의 클래스는 삭제
elem.setAttribute('class', 'box');
```

> 어떤 값을 알고 싶을 때는 get, 지정하고 싶을 때는 set, 있는지 없는지 묻고 싶을 때는 has를 주로 붙인다.


<br />

### 4. `classList`
classList 자체는 읽기 전용 프로퍼티이지만, `add()`, `remove()`, `toggle()` 메소드를 통해 변경할 수 있다.
```js
// 해당 요소에 box 클래스를 추가
elem.classList.add('box');

// 해당 요소에 box 클래스를 제거
elem.classList.remove('box');

// 해당 요소에 box 클래스가 있으면 제거, 없으면 추가
elem.classList.toggle('box');

// 해당 요소에 box 클래스가 있으면 true를, 없으면 false를 리턴
const hasBoxClass = elem.classList.contains('box');
```

<br />

## DOM Events

<br />

### Event란 무엇인가
event란, 웹에서 발생하는 사건들을 통칭하는 단어이다. 브라우저 입장에서는 사용자가 어떤 행동을 할 지 모르기 때문에, **사용자가 어떤 행동을 하면 이런 식으로 처리** 하라는 로직을 쌓아가는 것이 Event다. 

<br />

#### 주로 사용되는 DOM Event Types

1. load - 스타일시트, 이미지파일 등이 모두 load됐을 때 실행되는 이벤트
2. scroll - 사용자가 scroll할 때 실행되는 이벤트 
3. resize - 사용자가 화면 사이즈를 줄이거나 늘릴 때 실행되는 이벤트
4. blur - 사용자가 어떤 요소를 focus 했다가 다른 요소를 선택할 때 실행되는 이벤트
5. focus - 사용자가 어떤 요소를 클릭을 했거나, focus 상태일 때 실행되는 이벤트
6. change - input, textarea 등 요소의 값이 바뀌었을 때 실행되는 이벤트
7. submit - 사용자가 submit 버튼을 눌렀을 때 실행되는 이벤트
8. click - 사용자가 클릭했을 때 실행되는 이벤트 (dblclick은 버그가 많다)
9. mousedown - 사용자가 마우스를 눌렀을 때 실행되는 이벤트
10. mouseenter - 사용자가 마우스가 진입할 때 실행되는 이벤트
11. mouseleave - 사용자가 마우스가 나갈 때 실행되는 이벤트
12. mouseup - 사용자가 마우스를 눌렀다가 손을 뗄 때 실행되는 이벤트
13. keydown - 사용자가 특정 키를 눌렀을 때 실행되는 이벤트
14. touchstart - 모바일에서 사용자가 터치를 했을 때 실행되는 이벤트
15. touchmove - 모바일에서 사용자가 터치한 채로 이동할 떄 실행되는 이벤트
16. touchend - 모바일에서 사용자가 터치를 뗐을 때 실행되는 이벤트
17. DOMContentLoaded - 초기 HTML문서를 완전히 불러왔을 때 실행되는 이벤트


<br />

### Event Handler
브라우저에는 많은 이벤트들이 있다. 그 이벤트를 이런상황일 때 이렇게 처리해주겠다는 함수를 연결해주는 것을 **event handler(listener, callback function)** 이다. 

따라서 우리는 각각의 상황에 맞게 여러가지 handler를 만들어주면 된다. 이때 사용되는 보편적인 메소드가 `addEventListener()` 이다.

어떤 이벤트를 만들기 위해서는 누구한테 이벤트가 발생할 지가 필요하고, **~한테 ~가 일어나면 ~를 실행하겠다!** 가 Event의 기본 작성법이다.
```js
// elem 요소한테 click이 일어나면 clickHandler함수를 실행
elem.addEventListener('click', clickHandler);
// heading 요소한테 mouseenter가 일어나면 mouseEnterHandler함수를 실행
heading.addEventListener('mouseenter', mouseEnterHandler);
```

<br />

## Event Flow
프론트엔드 개발자라면 이벤트의 사용법을 아는 것 뿐 아니라, 이벤트가 어떤 식으로 작동하는 지 이해할 필요가 있다. 

모든 HTML 문서는 부모와 자식간의 관계로 중첩되어 구성된다.
예를 들어 `<div>` 태그에 클릭 이벤트가 발생했을 때, `<div>`를 클릭한다고 하더라도, `<div>`만 클릭했다고 보기엔 애매하다. `<div>`를 감싸고 있는 `<body>`, `<html>` 모두 중첩되어 있기 때문이다.

위 상황에서 `<div>`태그는 이벤트의 시발점이 되고, `<body>`태그와 `<html>`태그는 이벤트 탑승에 하게 된다. 

브라우저는 `<body>`와 `<html>`에도 click 이벤트가 있으면, `<div>`를 클릭했을 때 도미노처럼 다같이 click 이벤트가 실행된다. (click이벤트가 없다면 문제 없음!) 

<br />

### currentTarget 과 target의 차이
currentTarget은 이벤트의 실제적인 주인이고, target은 이벤트가 누구때문에 실행이 됐는지로 정해진다. 위 상황에서 `<div>`를 클릭했을 때,
- `<div>` : 이벤트의 주인은 자기 자신이고, 자기자신 때문에 이벤트가 실행됐기 때문에 currentTarget과 target 모두 `<div>` 를 가르킨다.
- `<body>` : 이벤트의 주인(currentTarget)은 자기 자신이고, 이벤트가 실행된 원인은 `<div>`이기 때문에 target은 `<div>`가 된다.
- `<html>` : 이벤트의 주인(currentTarget)은 자기 자신이고, 이벤트가 실행된 원인은 `<div>`이기 때문에 target은 `<div>`가 된다.

<br />

### 중첩된 이벤트의 순서
`<div>`, `<body>`, `<html>` 모두 click 이벤트가 있다면 `<div>`를 클릭했을 때, `<body>`와 `<html>` 또한 click 이벤트를 실행시켜야 하기 때문에 브라우저는 **어떤 순서로**로 실행을 시켜야하는 가에 대한 문제가 생긴다. 그 순서를 정하기 위해 Event Flow(흐름)를 갖게 된다. 

<img width="1440" alt="Event Flow" src="https://user-images.githubusercontent.com/59480963/106371397-1f416600-63a7-11eb-8b03-eb1cdd88f605.png">

currentTartget과 target이 일치하지 않는 경우, 이벤트가 발생했을 때 capture 단계에서 이벤트를 실행할지 bubble 단계에서 이벤트를 실행할지 선택할 수 있다. (default는 bubble)

capture 단계에서 실행되면 bubble 단계에선 실행되지 않고, bubble 단계에서 실행되면 capture 단계에선 실행되지 않는다. (웬만하면 bubble..)

`addEventListener()`는 3개의 인자를 받을 수 있는데, 1번째는 Event type, 두번째는 listener, 세번째에 useCapture를 Boolean 값으로 넣을 수 있다.











<br />
<br />
<br />

##### 출처
- [바닐라코딩](https://book.vanillacoding.co/bootcamp-prep/week-2/2.dom-review/2-1.-dom-introduction)
- [김버그Kimbug](https://youtu.be/CFgXIJ3RZ50)