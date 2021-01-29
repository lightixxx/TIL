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

### document.getElementById('id 명')
아이디는 기본적으로 하나의 HTML에서 고유한 값이어야 하기 때문에, 단 하나의 요소가 선택된다. 

그 하나의 요소는 Node 혹은 HTML Element라고 부르는 것이다. Node가 조금 더 포괄적인 상위 개념이고, HTML Element는 한 단계 하위 개념이다.

<br />

### document.getElementByClassName('class 명')
class는 HTML에서 주로 여러개를 그룹지어 사용하기 때문에 `getElementByClassName()` 함수를 이용해서 선택할 경우 모두 배열과 유사한 형태가 된다. 그리고 그 유사배열에 담긴 배열의 요소들이 하나의 HTML Element이다. 따라서 거의 대부분의 상황에서 배열의 인덱스 위치를 이용해서 사용해야 한다.

<br />

### document.getElemenetByTagName('tag 명')
특정 태그를 사용한 요소들을 선택할 수 있는 함수다. 해당 태그가 여러개라면 `getElementByClassName()`와 마찬가지로 유사배열의 형태로 요소를 가져온다.


<br />

### document.querySelector('CSS 선택자')
CSS 선택자 문법을 이용해서 요소를 선택할 수 있다. ID, Class, tagName 등 간편하게 선택할 수 있기 때문에 가장 많이 사용되는 방법이다.


<br />

## Element Nodes
Element는 HTML 태그와 같은(?) 뜻이다. 즉 HTML 태그는 Element이자 요소이다. 사용자의 행동을 예측해서 정적인 상태인 HTML에 개입해 속성을 바꿀 때 필요한 것이 DOM이다. 이것을 염두하고 공부하면 맥락을 파악하기 쉽다.

- createElement()
- getAttribute()
- setAttribute()
- classList()

### `cretateElement(tagName)`
지정한 `tagName`의 HTML 요소를 만들어서 반환한다.
```js
// h1 요소를 만들어서 heading이라는 변수에 할당
const heading = document.createElement('h1');
```
> 주의할 것은 자바스크립트로 생성한 요소는 직접 화면에 명시적으로 추가하기 전까지 화면에 나타나지 않는다. 즉, 생성만 했을 뿐, 화면에 추가하지는 않은 상태이다.

<br />

### `getAttribute(attributeName)`
해당 요소의 지정된 값을 반환한다. 존재하지 않는 속성이라면 null이나 ""(빈문자열)을 반환한다.
```js
// 해당 요소의 href 값을 attribute라는 변수에 할당
const attribute = elem.getAttribute('href');
```

<br />

### `setAttribute(attributeName, value)`
해당 요소에 속성과 값을 세팅한다.
```js
// 해당 요소에 href 값을 http://www.lightix.com로 세팅
elem.setAttribute('href', 'http://www.lightix.com');
```

<br />

### classList
classList 자체는 읽기 전용 프로퍼티이지만, `add()`, `remove()`, `toggle()`을 통해 변경할 수 있다.
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
<br />
<br />

##### 출처
- [바닐라코딩](https://book.vanillacoding.co/bootcamp-prep/week-2/2.dom-review/2-1.-dom-introduction)
- [김버그Kimbug](https://youtu.be/CFgXIJ3RZ50)