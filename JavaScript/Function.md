# Function (함수)

## "먹뱉..?"
함수는 쉽게 말해서 먹고 뱉는 것이다. 어떤 input을 함수에게 주면 함수는 연산과정을 통해 어떤 output을 주는 기능을 한다.

<br />

프로그램을 구성하는 가장 기본적인 빌딩 블록이면서 재사용이 가능한 서브 프로그램이라고 볼 수 있다. 주로 한 가지의 일을 수행하거나 값을 계산한다. 함수는 객체로 간주되기 때문에 변수에 할당할 수 있고, 매개변수로 함수를 전달할 수도 있고, 리턴할 수도 있다.

- 코드 로직을 나열하다 보면 코드가 너무 길어져서 이해하기 힘들어 질 때 사용한다.
- 특정 코드 구문이 여러 곳에서 중복되는 경우 사용한다.
- 코드가 둘 이상의 로직을 한 곳에 담고 있다면 의미를 명확하게 하기 위해서 함수를 사용해서 구분한다.

작명법 : doSomething, command, verb

<br />

## 📌 여기서 꼭 알아야 할 용어
- Call (호출) : 함수 내부의 코드를 실행하는 것을 호출이라고 한다.
- Parameter (매개변수) : 함수에 자료 값을 넘기기 위해 사용하는 것을 매개변수라고 한다.
- Return (리턴) : 함수를 실행한 결과로 나오는 것을 리턴이라고 한다.
- Callback Function (콜백함수) : 함수의 매개변수로 함수를 전달할 때, 해당 함수를 콜백함수라고 부른다.

<br />

## 함수를 정의하는 방법
함수는 크게 3가지 방식으로 정의할 수 있다.
```jsx
function f() { } // 함수 선언문 function declaration
const f = fuction() { } // 함수 표현식 function expression
const f00 = new Function('', '') // Function 생성자 함수 
```

<br />

### 함수 선언문 (Function declaration)
`function` 키워드와 함수명, 파라미터, 코드블럭으로 구성되어 있다.
- 함수명: 함수 선언문에서 함수명은 생략할 수 없다. 함수명은 코드블럭에서 자기 자신을 호출하거나, 디버거가 해당 함수를 구분할 수 있는 식별자이다.
- 파라미터(매개변수): 소괄호로 감싼 형태로 함수에 자료 값을 넘기기 위해 사용하는 것을 말한다.
- 함수 몸체(코드블럭): 중괄호로 감싼 코드블럭으로 함수명으로 함수가 호출되었을 때 실행되는 문들의 집합이다. `return`문으로 결과값을 반환할 수 있다.

```jsx
function printHello() {
	console.log('Hello');
}
printHello();
// 이런 함수는 사용자가 Hello만 출력할 수 있기 때문에 유용하지 않다.
```

```jsx
function printMessage(message) {
	console.log(message);
}
printMessage('Hello');
// 이런 식으로 사용자가 입력한 값을 출력해주는 함수를 만들 수 있다.
```

자바스크립트에서 함수는 '값'이다.

<br />

### 함수 표현식(function expression)
함수 리터럴 방식으로 함수를 정의하고, 변수에 할당하는 방식을 함수 표현식이라고 한다.

함수는 일급객체이므로 다음과 같은 특징이 있다.
- 무명의 리터럴로 표현이 가능하다.
- 변수나 자료 구조(배열, 객체 등)에 저장할 수 있다.
- 함수의 매개변수로 전달할 수 있다.
- 리턴 값으로 사용할 수 있다.
```jsx
const printMessage = function(message) {
	console.log(message);
}
```
함수 표현식으로 정의한 함수는 함수명을 생략하는 것이 일반적이다. 이런 함수를 익명함수라고 한다.

```jsx
//유명 함수
const foo = function printMessage(message) {
	console.log(message);
};

//익명 함수
const foo2 = function(message) {
	console.log(message);
};

foo('hello'); // hello
printMessage('error?'); // Uncaught ReferenceError: printMessage is not defined!
foo2('bye'); // bye
```
함수가 할당된 변수를 사용해서 호출하지 않고, 유명 함수의 함수명을 사용해 호출하면 에러가 발생한다. 함수 표현식에서 사용한 함수명은 외부 코드에서 접근이 불가능하기 때문이다.

함수는 변수에 할당할 수 있는데 이 변수는 함수명이 아니라 할당된 함수를 가리키는 참조값을 저장하게 된다. 함수 호출시 함수명이 아니라 함수가 가리키는 변수명을 사용해야 한다.

함수 선언문으로 정의한 함수 `printMessage`의 경우, 함수명으로 호출할 수 있었는데 이는 자바스크립트 엔진이 다음과 같이 해석한 것이다.
```jsx
const printMessage = function printMessage(message) {
	console.log(message);
}
printMessage('Hello');
```
함수명과 참조값을 가진 변수명이 일치해서 함수명이 호출된 것처럼 보이지만 변수명으로 호출된 것이다.

<br />

### Function 생성자 함수
함수 선언문과 함수 표현식은 사실상 함수 리터럴 방식으로 함수를 정의한다. 결국 내장 함수인 `Function` 생성자 함수로 생성하는 것을 단순화한 것이다. 일반적으로 사용하지는 않는다.
```jsx
const printMessage = new Function('message','console.log(message)');
printMessage('Hello');
```

## 함수의 호이스팅
위 3가지의 함수를 정의하는 방법은 동작 방식에 약간 차이가 있다.
```jsx
const printHello = printMessage('Hello');

function printMessage(message) {
	console.log(message);
}
```
함수 선언문으로 함수가 정의되기 이전에 함수를 호출할 수 있다. 함수 선언문은 선언된 위취와 상관없이 코드 내에 어디서든 호출이 가능한데, 이것을 함수 호이스팅이라고 한다.

> 자바스크립트는 `var` 뿐만 아니라 ES6의 `let`, `const`를 포함한 모든 선언을 호이스팅한다. 즉, 자바스크립트는 모든 선언문 (`var`, `let`, `const`, `function`, `class` 등)이 선언되기 이전에 참조가 가능하다.

함수 선언문으로 정의된 함수는 스크립트가 로딩되는 시점에 바로 함수 선언, 초기화, 할당이 한 번에 이루어 진다. 그렇기 때문에 함수 선언의 위치와는 상관없이 소스 내 어느 곳에서든 호출이 가능하다.

반면에 함수 표현식으로 함수를 정의한 경우에는 에러가 발생한다.
```jsx
const printHello = printMessage('Hello'); // Uncaught ReferenceError: Cannot access 'printMessage' before initialization

const printMessage = function(message) {
	console.log(message);
}
```
함수 표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생한다. ES6에 등장한 `let`과 `const` 키워드로 선언된 변수를 선언문 이전에 참조하면 참조 에러가 발생한다. 이것은 `let` 키워드로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(TDZ)에 빠지기 때문이다.

또한 `var` 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한 번에 이루어지기 때문에 스코프에 변수를 등록하고 메모리에 변수를 위한 공간을 확보한 뒤 `undefined`로 초기화 한다. 따라서 변수 선언문 이전에 변수에 접근해도 스코프에 변수가 존재하기 때문에 에러가 발생하지 않지만 `undefined`를 반환한다.

<br />

**Q. 선언적 함수와 함수 표현식의 호이스팅 정리**

- 함수 표현식은 변수에 할당된 다음 부터 호출을 할 수 있지만, 선언적 함수는 자바스크립트가 내부적으로 선언된 함수를 가장 먼저 메모리에 올리기 때문에(호이스팅) 선언되기 이전에 호출해도 실행이 된다.

```jsx
hello1(); // OK
hello2(); // hello2 is not a function
hello3(); // hello3 is not defined

function hello1() {
	console.log('hello1');
}

var hello2 = function() {
	console.log('hello2');
}

const hello3 = function() {
	console.log('hello3');
}
```

호이스팅도 추후에 [여기서](https://github.com/lightixxx/TIL/blob/master/JavaScript/learnMore/hoisting.md) 더 알아보는 걸로..

<br />

## Parameters (매개변수)
함수에 자료 값을 넘기기 위해 사용하는 것을 매개변수라고 한다.
- 매개변수는 함수 내에서 변수와 동일하게 동작한다.
- 메모리에 값이 저장되어서 값이 그대로 전달된다.
- 객체 매개변수는 메모리에 레퍼런스로 저장되어서 레퍼런스가 전달된다.
```jsx
function changeName(obj) {
	obj.name = 'coder';
}
const lightix = {name: 'lightix'};
changeName(lightix);
console.log(lightix); // {name: 'coder'}
```

<br />

### 매개변수와 인수
매개변수는 함수 내에서 변수와 동일하게 메모리 공간을 확보하고, 함수에 전달한 인수는 매개변수에 할당된다. 
```jsx
const printMessage = function(message, name) {
	console.log(`${message}, ${name}!`);
}
printMessage('Hello'); // Hello, undefined!
```
인수를 전달하지 않으면 `undefined`로 초기화된다.

<br />

### Call-by-value VS Call-by-reference
원시타입 인수는 값에 의한 호출로 동작한다. 이는 함수를 호출할 때 원시 타입 인수를 매개변수로 전달할 때 값을 복사해서 함수로 전달된다. 따라서 함수 내에서 매개변수의 값이 변경되어도 전달이 완료된 원시타입 값은 변경되지 않는다.

반면 객체형(참조형) 인수는 참조에 의한 호출로 동작한다. 이는 함수를 호출할 때 참조 타입 인수를 매개변수로 전달할 때 값이 복사되는 것이 아니라 객체의 참조값이 매개변수에 저장되어서 함수로 전달된다. 따라서 함수 내에서 매개변수를 통해 객체의 값을 변경했을 때 전달된 참조형의 인수값도 같이 변경된다.
```jsx
let num = 0;
const obj = {name: 'Lee'}

function changeVal(primitive, obj) {
	primitive += 100;
	obj.name = 'Kim';
}


console.log(num); // 0
console.log(obj.name); // 'Lee'

changeVal(num, obj);

console.log(num); // 0
console.log(obj.name); // 'Kim'
```

<br />

## Return
함수는 자신을 호출한 코드에게 수행한 결과를 반환한다.
- `return` 키워드는 함수를 호출한 코드에게 값을 리턴한다.
- 배열 등 을 이용해서 한 번에 여러 개의 값을 리턴할 수 있다.
- 반환을 생략할 경우 암묵적으로 `undefined`를 리턴한다.
- `return` 키워드를 만나면 함수의 실행을 중단한 후, 함수를 호출한 코드로 돌아간다.
- `return` 키워드 이후의 다른 구문은 실행되지 않는다.


### Early return

```jsx
// bad
function upgradeUser(user) {
	if(user.point > 10) {
		// long upgrade logic...
	}
}

// good
function upgradeUser(user) {
	// 조건이 맞지 않는 경우, undefined인 경우, 값이 -1인 경우
	// 빨리 return을 하고 긴 로직을 실행하는 것이 바람직하다
	if (user.point <= 10) {
		return;
	}
	// long upgrade logic...
}
```

<br />

## 함수 객체의 프로퍼티
자바스크립트에서 함수는 객체이다. 따라서 함수도 프로퍼티를 가질 수 있다.
```jsx
function square(num) {
	return num * num;
}

square.x = 10;
square.y = 20;

console.log(square.x, square.y);
```
함수 객체는 일반 객체와 달리 함수 객체만의 프로퍼티를 갖고있다.

<br />

### arguments 프로퍼티
arguments 객체는 함수 호출 시 전달된 인수(arguments)들의 정보를 담고 있는 순회가능한 유사배열 객체이며 함수 내부에서 지역변수처럼 사용된다. 즉, 함수 외부에서는 사용할 수 없다.

자바스크립트는 함수 호출 시 함수 정의에 따라 인수를 전달하지 않아도 에러가 발생하지 않는다.
```jsx
function multiply(x, y) {
	console.log(arguments);
	return x * y;
}

multiply();
multiply(1);
multiply(2,4);
multiply(2, 4, 6);
```
매개변수(parameter)는 인수(argument)로 초기화된다.
- 매개변수의 갯수보다 인수를 적게 전달했을 경우, 인수가 전달되지 않은 매개변수는 `undefined`로 초기화된다.
- 매개변수의 갯수보다 인수를 더 많이 전달한 경우, 초과된 인수는 무시된다.

> 이 특성때문에 런타임시 호출된 함수의 인자 갯수를 확인하고 이에 따라 동작을 달리 정의할 필요가 있을 수 있다. 이때 유용하게 사용되는 것이 arguments 객체이다...?

arguments 객체는 매개변수의 갯수가 확정되지 않은 가변 인자 함수를 구현할 때 유용하게 사용된다.

```jsx
function sum() {
	let result = 0;

	for(let i = 0, i < arguments.length; i++) {
		result += arguments[i];
	}

	return result;
}

console.log(sum()); // 0
console.log(sum(2, 3)); // 5
console.log(sum(2, 3, 4)); // 9
```
자바스크립트는 함수를 호출할 때 인수들과 함께 암묵적으로 arguments 객체가 함수 내부로 전달된다. arguments 객체는 배열의 형태로 인자값 정보를 담고 있지만 실제 배열이 아닌 유사배열객체이다. 

> 유사배열객체란, length 프로퍼티를 가진 객체를 말한다. 유사배열객체란 배열이 아니므로 배열의 메소드는 사용하면 에러를 발생시킨다.


그 밖에 caller, length, name, __proto__ 접근자, prototype 등 다양한 프로퍼티는 나중에 필요하면 배우자.. 머리 터지겠다.

<br />

## 함수의 다양한 형태

### IIFE (Immediately Invoked Function Expression)
함수를 선언함과 동시에 호출하는 것을 말한다. 최초 한번만 호출되며 다시 호출할 수 없다. 이러한 특징을 이용해서 최초 한번만 실행이 필요한 초기화 처리 등에 사용할 수 있다.
```jsx
(function hello() {
	console.log('IIFE');
})();
```

> 자바스크립트에서 가장 큰 문제점 중의 하나는 파일이 분리되어 있다하여도 글로벌 스코프가 하나이며 글로벌 스코프에 선언된 변수나 함수는 코드 내의 어디서든지 접근이 가능하다는 것이다.
> 
> 따라서 다른 스크립트 파일 내에서 동일한 이름으로 명명된 변수나 함수가 같은 스코프 내에 존재할 경우 원치 않는 결과를 가져올 수 있다. 
> 
> 즉시 실행 함수 내에 처리 로직을 모아 두면 혹시 있을 수도 있는 변수명 또는 함수명의 충돌을 방지할 수 있어 이를 위한 목적으로 즉시실행함수를 사용되기도 한다.
> 
> 특히 jQuery와 같은 라이브러리의 경우, 코드를 즉시 실행 함수 내에 정의해 두면 라이브러리의 변수들이 독립된 영역 내에 있게 되므로 여러 라이브러리들은 동시에 사용하더라도 변수명 충돌과 같은 문제를 방지할 수 있다. [출처 - poiemaweb](https://poiemaweb.com/js-function)

<br />

### 내부 함수
함수 내부에 다른 함수를 정의하는 것을 말한다. 내부 함수인 자식함수는 부모함수의 변수에 접근할 수 있지만 부모 함수는 자식함수의 변수에 접근할 수 없다.

<br />

### Callback 함수
함수를 명시적으로 호출하는 방식이 아니라 특정 이벤트가 발생했을 때, 시스템에 의해 호출되는 함수를 말한다. 함수의 파라미터로 함수가 전달되어 어느 특정 시점에 실행되는 것을 말한다.
```jsx
function randomQuiz(answer, printYes, printNo) {
	if(answer == 'lightix') {
		printYes();
	} else {
		printNo();
	}
}

// 익명함수 (anonymous function)
const printYes = function () {
	console.log('Yes!');
};

// 유명함수(Named function)
// 함수안에서 자기를 호출해서 무한 반복시킬 때 사용
const printNo = function print() {
	console.log('No!');
}

randomQuiz('wrong', printYes, printNo);
randomQuiz('lightix', printYes, printNo);
```

> 콜백 함수는 주로 비동기식 처리 모델에 사용된다. 처리가 종료되면 호출될 함수를 미리 매개변수에 전달하고 처리가 종료되면 콜백함수를 호출하는 것을 비동기식 처리 모델이라고 한다. 콜백함수는 콜백 큐에 들어가 있다가 해당 이벤트가 발생하면 호출된다. 콜백함수는 클로저 이므로 콜백 큐에 단독으로 존재하다가 호출돼도 콜백함수를 전달받은 함수의 변수에 접근할 수 있다. [출처 - poiemaweb](https://poiemaweb.com/js-function)

<br />

## ES6에 추가된 문법

<br />

### Default parameters (ES6)
매개변수가 전달되지 않았을 때 default 값을 설정해서 출력할 수 있다.

```jsx
// 예전 문법에서는 파라미터가 전달되지 않았을 때, undefined로 출력되는 것을 막기위해 이런 방법을 썼다
function showMessage(message,from) {
	if(from === undefined){
		from = 'unknown';
	}
	console.log(`${message} by ${from}`);
}
showMessage('Hi!');

// 매개변수가 하나만 전달되었을 경우 디폴트값을 설정할 수 있다 (ES6)
function showMessage(message, from = 'unknown') {
	console.log(`${message} by ${from}`);
}
showMessage('Hi!');
```

<br />

### Rest Parameters(ES6)
배열의 형태로 전달되는 파라미터이다.

```jsx
function printAll(...args) {
	for (let i = 0; i < args.length; i++) {
		console.log(args[i]);
	}

	// 간편한 방법
	for (const arg of args) {
		console.log(arg);
	}

	// 더 간편한 방법 (배열의 내장함수 이용)
	args.forEach((arg) => console.log(arg));
}
printAll('lightix', 'lvvrvsh', 'sogeumnam');
```

<br />

### Arrow function
익명함수로 만들고 변수에 할당한다.

```jsx
const simplePrint = () => console.log('simplePrint');
const add = (a, b) => a + b;

// 복잡한 경우에는
const simpleMultiply = (a, b) => {
	// do something more
	return a * b;
}
```
