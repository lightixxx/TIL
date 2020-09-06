# Function (함수)

프로그램을 구성하는 가장 기본적인 빌딩 블록이면서 재사용이 가능한 서브 프로그램이라고 볼 수 있다. 주로 한 가지의 일을 수행하거나 값을 계산한다. 함수는 객체로 간주되기 때문에 변수에 할당할 수 있고, 매개변수로 함수를 전달할 수도 있고, 리턴할 수도 있다.

- 코드 로직을 나열하다 보면 코드가 너무 길어져서 이해하기 힘들어 질 때 사용한다.
- 특정 코드 구문이 여러 곳에서 중복되는 경우 사용한다.
- 코드가 둘 이상의 로직을 한 곳에 담고 있다면 의미를 명확하게 하기 위해서 함수를 사용해서 구분한다.

작명법 : doSomething, command, verb

<br />

**🚨 Basic Syntax 🚨**

```jsx
function printHello() {
	console.log('Hello');
}
printHello();
// 이런 함수는 사용자가 Hello만 출력할 수 있기 때문에 유용하지 않다.
```

```jsx
function log(message) {
	console.log(message);
}
log('Hello');
// 이런 식으로 사용자가 입력한 값을 출력해주는 함수를 만들 수 있다.
```

자바스크립트에서 함수는 '값'이다.

```jsx
const f = fuction() { } // 함수 표현식 function expression
function f() { } // 함수 선언문 function declaration
```

표현의 차이일 뿐 별 의미는 없다.

<br />

## **Parameters (매개변수)**

- 메모리에 값이 저장되어서 값이 그대로 전달된다.
- 객체 매개변수는 메모리에 레퍼런스가 저장되어서 레퍼런스가 전달된다.

```jsx
function changeName(obj) {
	obj.name = 'coder';
}
const lightix = {name: 'lightix'};
changeName(lightix);
console.log(lightix); // {name: 'coder'}
```

<br />

## Default parameters (ES6)

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

## Rest Parameters(ES6)

배열의 형태로 전달되는 파라미터이다

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
printAll('dream', 'coding', 'ellie');
```

<br />

## Local scope

- 블록 밖에서는 안에 접근할 수 없고, 블록 안에서는 밖에 접근할 수 있다

```jsx
let globalMessage = 'global'; // global variable 전역변수

function printMessage() {
	let message = 'hello';
	console.log(message); // local variable 지역변수
	console.log(globalMessage);
}

printMessage();
console.log(message); // 밖에서 안에 선언된 변수에 접근했기 때문에 Error
```

중첩된 함수에서 자식에 선언된 함수가 부모에 선언된 변수들에 접근이 가능하게 하는 것이 클로저!

<br />

## Return

- 함수에서는 매개변수의 값들을 전달받아서 계산된 값을 리턴할 수 있다

```jsx
function sum(a,b) {
	return a + b;
}

const result = sum(1, 2); // 3
```

<br />

## Early return

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

## Function Expression

익명 함수를 변수에 할당하는 것을 말한다.

```jsx
const print = function() {
	console.log('print');
}
print(); // print
const printAgain = print;
printAgain(); // print
```

**Q. 선언적 함수와 함수 표현식의 차이점**

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

<br />

## Callback

함수의 파라미터로 함수가 전달되어 사용하는 것을 콜백함수라고 한다.

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

<br />

## Arrow function

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

<br />

## IIFE (Immediately Invoked Function Expression)

함수를 선언함과 동시에 호출하는 것을 말한다.

```jsx
(function hello() {
	console.log('IIFE');
})();
```
