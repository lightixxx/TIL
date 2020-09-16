# scope
변수를 사용할 수 있는 코드는 변수가 선언된 위치에 따라 달라진다. 만일 변수를 함수 내에 선언했으면 그 변수는 함수 내에서만 사용할 수 있다. 이렇게 변수가 사용 가능한 영역(참조 범위)을 변수의 범위(scope)라고 한다. 스코프가 없다면 같은 식별자 이름은 충돌을 일으키기 때문에 프로그램 전체에서 하나밖에 사용하지 못하게 된다. 예를 들어 컴퓨터에 폴더가 하나밖에 없다면 같은 이름을 갖는 파일을 하나밖에 생성하지 못하는 것과 같은 개념이다.

자바스크립트의 변수는 블록 레벨 스코프를 가지지 않고, 함수 레벨 스코프를 갖는다. 단, ES6에서 도입된 let, const 키워드를 사용하면 블록 레벨 스코프를 사용할 수 있다.

- 전역 Scope (Global scope) : 코드 어디에서든지 참조할 수 있다. 전역 객체인 `window`의 프로퍼티이다.
- 지역 Scope (Local scope) : 정의된 함수 내에서만 참조할 수 있다.
- 블록 Scope (Block scope) : if, for, switch 등 특정 블록 내부에서만 참조할 수 있다.
- 함수 Scope (Function scope) : 함수 내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없다. 즉, 함수 내부에서 선언된 변수는 지역 변수이며, 함수 외부에서 선언한 변수는 모두 전역변수이다.

전역 변수는 항상 메모리에 저장되기 때문에 최소한으로 사용하는 것이 좋다.

```jsx
// block scope
var a = 10;
if(true) {
	var a = 20;
	console.log(a); // 20
}
console.log(a); // 20

// function scope
var b = 10;
function hello() {
	var b = 20;
	console.log(b); // 20
}
hello();
console.log(b); // 10
```
함수 내에서 함수를 재선언 하는 경우 `var`는 function scope 내에서만 유효하기 때문에 함수 내부에서 `var` 키워드를 재선언 한 것은 바깥에서 독립적으로 실행된다.

<br />

## `var` 키워드로 선언된 변수의 문제점
1. 함수 레벨 스코프
   * 전역 변수의 남발
   * for loop 초기화 식에서 사용한 변수를 for loop 외부 또는 전역에서 참조할 수 있다.
2. `var` 키워드 생략 가능
   * 의도하지 않은 변수의 전역화
3. 중복 선언 허용
   * 의도하지 않은 변수값 변경
4. 변수 호이스팅
   * 변수를 선언하기 전에 참조가 가능

<br />

대부분의 C-family 언어들은 블록 레벨 스코프를 따르는 반면 자바스크립트의 `var` 는 함수 레벨 스코프를 따른다. ES6의 `let` 은 블록 레벨 스코프를 따르기 때문에 `let`을 사용하자!

<br />

### `let` VS `var`
```jsx
var x = 0;
{
	var x = 1;
	console.log(x); // 1
}
console.log(x); // 1

let y = 0;
{
	let y = 1;
	console.log(y); // 1
}
console.log(y); // 0
```

```jsx
let globalName = 'global name';
{
	let name = 'lightix';
	console.log(globalName); // 전역변수이기 때문에 안에서 접근이 가능하다
}

console.log(name); // 지역변수이기 때문에 밖에서 접근이 불가능하다
console.log(globalName); // 전역변수이기 때문에 밖에서 접근이 가능하다
```
<br />

```jsx
// block scope
let a = 10;
if(true) {
	let a = 20;
	console.log(a); // 20
}
console.log(a); // 10

// function scope
let b = 10;
function hello() {
	let b = 20;
	console.log(b); // 20
}
hello();
console.log(b); // 10
```
`let`은 block이든 function이든 내부에 선언된 값이 밖으로 나오지 않는다.

function scope가 block scope를 포함한다.

```jsx
const value = 1;

function myFunction() {
	console.log(value); // 1
}

function otherFunction() {
	const value = 2;
	console.log(value); // 2
}

myFunction();
otherFunction();

console.log(value); // 1
```
처음 선언한 `value`는 Global Scope로 선언된 값이다. Global Scope로 선언된 값은 어디서든 사용이 가능하기 때문에 `myFunction`에서 '1'이 나온다.

`otherFunction` 에서 함수 내부에 `value` 값을 '2'로 새로 선언했다. 이 value 값은 Function Scope에 해당되기 때문에 otherFunction 내부에서만 유효한 값이 된다. 이렇게 값을 설정한다고 Global Scope로 선언된 `value` 값이 바뀌지는 않는다.

```jsx
const value = 1;

function myFunction() {
	const value = 2;
	const anotherValue = 3;
	function functionInside() {
		console.log(value); // 2
		console.log(anotherValue); // 3
	}
	functionInside();
}

myFunction();
console.log(value); // 1
console.log(anotherValue); // Error
```

`myFunction` 내부에 `anotherValue` 라는 새로운 값을 선언하고, `functionInside` 라는 함수를 선언했다. `functionInside` 함수에서 `myFunction` 에서 선언한 `value` 값과 `anotherValue` 값을 조회할 수 있다.

하지만, `myFunction` 밖에서는 `anotherValue` 를 조회할 수 없다

```jsx
const value = 1;

function myFunction() {
	const value = 2;
	if(true) {
		const value = 3;
		console.log(value); // 3
	}
	console.log(value); // 2
}

myFunction();
console.log(value); // 1
```

`const` 로 선언된 Block Scope로 선언된다. 따라서, if문 같은 블록 내에서 변수/상수를 선언하면, 해당 블록 내부에서만 사용이 가능하며, 블록 밖의 범위에서 똑같은 이름을 가진 값이 있다고 해도, 영향을 주지 않는다. `let` 도 마찬가지 !

하지만 `var`는 다르다.

```jsx
var value = 1;

function myFunction() {
	var value = 2;
	if(true) {
		var value = 3;
		console.log(value); // 3
	}
	console.log(value); // 3
}

myFunction();
console.log(value); // 1
```
`var` 는 Function Scope로 선언이 된다. 따라서 if 문 블록 내부에서 선언한 `value` 값이 블록 밖의 `value` 에도 영향을 미친다.

## 정적 스코프 vs 동적 스코프
```jsx
var x = 1;

function foo() {
	var x = 10;
	bar();
}

function bar() {
	console.log(x);
}

foo();
bar();
```
위 코드의 실행결과는 함수 `bar`의 상위 스코프가 무엇인지에 따라 결정된다.
1. 함수를 어디서 호출했는지
2. 함수를 어디서 선언했는지
에 따라 상위 스코프를 결정한다.

1번 방식은 `bar`의 상위 스코프는 함수 `foo`와 전역일 것이고, 2번 방식은 `bar`의 스코프는 전역일 것이다.
<br />

1번 방식은 동적스코프(Dynamic Scope)라고 하고, 2번 방식은 정적 스코프(Static Scope) 또는 렉시컬 스코프(Lexical Scope)라고 한다. 대부분의 프로그래밍 언어는 정적 스코프 방식을 따른다.

**정적 스코프는 함수를 어디서 호출하는지가 아니라 어디에 선언했는지에 따라 결정된다.**
함수를 선언한 시점에 상위 스코프가 결정되고, 함수를 어디에서 호출했는지는 아무런 의미가 없다. 위 예제에서 `bar`는 전역에 선언되었기 때문에 상위 스코프는 전역 스코프이고, 위 예제는 전역 변수 x의 값인 1을 두 번 출력한다.

<br />

## 암묵적 전역 변수
```jsx
var x = 10; // 전역변수

function foo() {
	y = 20; // 선언하지 않은 식별자
	console.log(x + y);
}

foo(); // 30
```
위 코드에서 `y = 20`은 선언하지 않은 식별자에 값을 할당한 것이다. 에러가 날 것 같지만 문제없이 동작한다. 그 이유는 선언하지 않은 식별자에 값을 할당하면 전역 객체의 프로퍼티(`window.y = 20`)로 해석되기 때문이다. 이런 현상을 암묵적 전역(implicit global)이라 한다.

주의해야 할 것은 `y`는 전역 객체의 프로퍼티로 추가된 것 뿐이라 변수가 아니다. 따라서 호이스팅이 발생하지 않는다.