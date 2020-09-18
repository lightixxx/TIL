# Global object (전역객체)
모든 객체의 최상위 객체를 의미하며, 브라우저에서는 `window`, 서버(Node.js)에서는 `global`객체를 의미한다.
- 전역 객체는 실행 컨텍스트에 컨트롤이 들어가기 이전에 생성이 되고, constructor가 없기 때문에 `new` 연산자로 전역 객체를 생성할 수 없다.
- 전역 객체는 전역 스코프를 갖는다.
- 전역 객체의 자식 객체를 사용할 때, 전역 객체는 생략할 수 있다.
- 전역 변수는 전역 객체의 프로퍼티가 된다.
- 전역에 선언한 함수는 전역 객체의 메서드가 된다.

<br />

## 전역 프로퍼티
전역에서 사용하는 값들을 나타내는 전역 객체의 프로퍼티이다. 주로 간단한 값이 대부분이고, 다른 프로퍼티나 메서드를 갖고 있지 않는다.

<br />

### Infinity
양수와 음수의 무한대를 나타내는 숫자값 Infinity를 갖는다.
```jsx
console.log(window.Infinity); // Infinity

console.log(3 / 0); // Infinity
console.log(-3 / 0); // Infinity
```

<br />

### NaN
숫자가 아님(Not a Number)을 나타내는 숫자값 NaN을 갖는다. Number.NaN 프로퍼티와 같다.

```jsx
console.log(window.NaN); // NaN

console.log(Number('lightix')); // NaN
console.log(5 * 'lightix'); // NaN
```

<br />

### undefined
primitive type `undefined`를 값으로 갖는다.
```jsx
console.log(window.undefined); // undefined

var name;
console.log(name); // undefined
```

## 전역 함수 (global function)
전역에서 호출할 수 있는 함수로 전역 객체의 메서드이다.

### eval()
