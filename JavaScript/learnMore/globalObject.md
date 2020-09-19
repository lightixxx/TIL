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


<br />

### isFinite()
매개변수에 전달된 값이 정상적인 유한수인지 검사해서 `true` or `false`로 반환한다. 숫자가 아닌 경우, 숫자로 변환해서 검사한다.
```jsx
console.log(isFinite(Infinity)); // false
console.log(isFinite(NaN)); // false

console.log(isFinite(10)); // true
console.log(isFinite('10')); // true '10' -> 10
console.log(isFinite(null)); // true null -> 0
```

<br />

### isNaN()
매개변수에 전달된 값이 NaN인지 검사해서 `true` or `false`로 반환한다. 숫자가 아닌 경우, 숫자로 변환해서 감사한다.
```jsx
isNaN(NaN)       // true
isNaN(undefined) // true: undefined → NaN
isNaN({})        // true: {} → NaN
isNaN('blabla')  // true: 'blabla' → NaN

isNaN(true)      // false: true → 1
isNaN(null)      // false: null → 0
isNaN(37)        // false

// strings
isNaN('37')      // false: '37' → 37
isNaN('37.37')   // false: '37.37' → 37.37
isNaN('')        // false: '' → 0
isNaN(' ')       // false: ' ' → 0

// dates
isNaN(new Date())             // false: new Date() → Number
isNaN(new Date().toString())  // true:  String → NaN
```

<br />

### parseFloat()
매개변수에 전달된 문자열을 부동소수점 숫자로 반환한다. 문자열의 첫 숫자만 반환되고, 전후 공백은 무시된다. 첫 문자를 숫자로 바꿀 수 없다면 NaN을 리턴한다.
```jsx
parseFloat('3.14'); // 3.14
parseFloat('10.00'); // 10
parseFloat('12 34 56'); // 12
parseFloat('28 years old'); // 28
parseFloat('I am 40 years old'); // NaN
```
<br />

### parseInt()
매개변수에 전달된 문자열을 정수형 숫자로 반환한다. 반환값은 10진수이다.

```jsx
parseInt(string, radix);
// string: 해석할 문자열
// radix: 진법을 나타내는 수 (2 ~ 36, default: 10)

parseInt(10); // 10
parseInt(12.345); // 12

parseInt('10'); // 10
parseInt('12.345'); // 12

parseInt(10, 2); // 10
parseInt(10, 8); // 10
parseInt(10, 16); // 10
```
자바스크립트는 0으로 시작하거나 0x로 시작하면 10진수가 아니라 각각 8진수, 16진수로 생각하고 변환한다.
```jsx
parseInt('0x273'); // 627
parseInt('273'); // 273
parseInt('0273'); // 187
```
두번째 매개변수에 진법을 입력하면 앞의 수를 해당 진법의 수로 인식한다.
```jsx
parseInt('FF', 16); // 255
parseInt('52', 10); // 52
parseInt('11', 8); // 9
parseInt('10', 2); // 2
```
 첫번째 매개변수에 전달된 문자열의 첫번째 문자가 해당 지수의 숫자로 변환될 수 없다면 NaN을 반환한다.
 ```jsx
parseInt('A9'); // NaN
parseInt('20', 2); // NaN
 ```
<br />

### eval()
매개변수에 전달된 문자열 또는 표현식을 평가 또는 실행한다. 사용자로 부터 입력받은 콘텐츠를 `eval()`로 실행하는 것은 보안에 취약하기 때문에 가급적으로 사용하지 말아야한다.

[출처 - poiemaweb](https://poiemaweb.com/js-global-object)