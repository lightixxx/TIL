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
<br />
<br />

##### 출처
- [바닐라코딩](https://book.vanillacoding.co/bootcamp-prep/week-2/2.dom-review/2-1.-dom-introduction)
- [김버그Kimbug](https://youtu.be/CFgXIJ3RZ50)