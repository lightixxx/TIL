# Basic Syntax

- 자바스크립트의 기본 문법 및 개념을 정리한 파일입니다.
- 비전공 프론트엔드 입문자가 이해한 만큼 작성했습니다.
<br />

## Expression
값을 만들어내는 간단한 코드를 표현식이라고 한다.

```jsx
true
20
100 + 20 + 3
"Hello" + " World"
```

표현식은 값을 만들어내기 때문에 함수의 인자로 사용할 수 있다.

```jsx
console.log(100 + 20 + 3);
alert("Hello" + " World");
```
<br />

## Statement
하나 혹은 여러 개의 표현식이 모여서 문장을 이룬다.
- 모든 표현식은 문장이 될 수 있다.
- 보통 문장의 끝에는 세미 콜론을 붙인다.

```jsx
const name = "lightix";
alert(name);
```

- 한 줄에 문장이 하나인 경우에는 세미 콜론을 붙이지 않아도 문제가 없지만 관례적으로 붙인다.
- 한 줄에 여러 문장을 적을 경우, 세미 콜론으로 문장을 구분해야 한다.
- 마지막 문장을 세미 콜론을 붙이지 않아도 문제가 없다.
- 여러 문장을 썼을 때, 마지막 문장의 결과가 반환된다.

```jsx
true; 20; 100+20+3 // 123
```

- 조건문 (if), 반복문 (for) 도 문장이다.
- 이 경우 마지막 } 뒤에 세미콜론을 붙이지 않는다.

### **✔️ 표현식이 모여서 문장이 되고, 문장들이 모여서 프로그램이 된다**
<br />

## Keywords & Reserved Words

### Keywords

자바스크립트에서 특정한 목적을 위해 사용하는 단어로 이러한 키워드들은 예약어로 지정되어 있다.

```jsx
const name = 'lightix' // const 라는 단어는 상수를 선언할 때 사용하는 키워드
```

### Reserved Words

프로그램을 작성할 때, 변수명, 함수명 등 이름으로 사용할 수 없는 단어.

```jsx
let return = 'lightix'; // return 은 예약어이기 때문에 변수명으로 사용할 수 없다
function for() {} // for 은 예약어이기 때문에 함수명으로 사용할 수 없다
```

### Reserved keywords

이미 특정한 목적을 위해 사용하기 때문에 사용할 수 없는 예약어. (런타임 환경마다 다를 수 있음)

[MDN- Reserved keywords](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Lexical_grammar#%ED%82%A4%EC%9B%8C%EB%93%9C)

### Future reserved keywords

앞으로 특정한 목적을 위해 사용할 가능성이 있어서 사용할 수 없는 예약어. (런타임 환경마다 다를 수 있음)

[Future_reserved_words](https://javascript.fandom.com/wiki/Future_reserved_words)

<br />

## Identifier (식별자)

코드 내의 변수, 함수, 속성을 식별하는 문자열.

```jsx
const name = 'lightix'; // 'lightix'라는 값은 name이라는 식별자로 부른다
function hello() {} // hello 라는 함수는 hello라는 식별자로 부른다
const person = {name: 'lightix', age: 28}; // name이 'lightix'이고, age가 28인 객체를 person이라는 식별자로 부른다
```

- 대소문자를 구분한다.

```jsx
var myName = 'lightix';
var myname = 'lightix'; // 두 변수는 다른 값
```

- 유니코드 문자 , $ , _ , 숫자(0-9) 를 사용할 수 있지만, 숫자로 시작할 수는 없다.
- 예약어는 사용할 수 없고, 공백 문자도 사용할 수 없다.

```jsx
const name1 = 'lightix'; // OK
const $name = 'lightix'; // OK
const _name = 'lightix'; // OK
const 이름 = 'lightix'; // OK, but use English
const 1name = 'lightix'; // Error!
```

✔️프로그램에서 사용하는 변수나 함수의 이름을 짓는 것은 언제나 어려운 일이다.

✔️의미없는 이름은 사용하지 않고, 역할에 맞는 적절한 이름을 짓도록 노력해야 한다.
<br />

## Comments (주석)

소스 코드에서 프로그램에 영향을 주지 않고, 무시되는 부분으로 보통은 소스코드를 이해할 수 있도록 돕는 역할로 사용한다.

```jsx
// 이 함수는 인사를 하는 함수입니다  <- 이렇게 주석으로 소스코드를 설명할 때 많이 사용한다
function hello() {}

/*
한줄
두줄
세줄
이렇게 여러 줄을 주석으로 사용할 수도 있다.
*/
```
<br />

## Data-type (자료형)

### Dynamic typing

자바스크립트는 변수를 선언할 때 어떤 타입인지 선언하지 않고, 런타임 때 할당된 값에 따라서 타입을 결정한다. 런타임 때 타입이 결정되기 때문에, 에러가 나는 경우가 많다.

```jsx
let text = 'hello'; // value: hello, type: string
text = 1; // value: 1, type: number
text = '7' + 5; // value: 75, type: string
text = '8' / '2'; // value: 4 , type: number
```

### 자바스크립트는 크게 두 가지 데이터 타입을 갖는다

1. Primitive data type : Number, String, Boolean 등과 같이 값이 전달되는 타입
2. Reference data type : Array, Object, Function 과 같이 참조로 전달되며, 포인터 주소만 복사하고 동일한 데이터를 모두 공유하는 타입

### Variable types

- 더이상 작은 단위로 나누어지지 않는 단일 아이템 : number, string, boolean, null, undefined, symbol
- 단일 아이템을 여러개 묶어서 한 박스로 관리할 수 있는 아이템 : object
- 함수는 1급 객체이다

### Number

숫자를 다루기 위한 데이터 타입이다.

- 타 언어와 달리 정수, 소수점 모두 number type

```jsx
const infinity = 1 / 0; // 양수를 0으로 연산하면 infinity
const negativeInfinity = -1 / 0; // 음수를 0으로 연산하면 negativeInfinity
const nan = 'not a number' / 2 ; // 숫자가 아닌 값을 연산하면 NaN

// bigInt (자바스크립트에서는 (-2**53) ~ (2**53) 까지만 표현이 가능하지만
const bigInt = 123698149817298693486723459823465923487324n; // 숫자 끝에 n을 붙이면 bigInt로 값이 나온다
```

- NaN 는 숫자가 아니라는 의미의 숫자이다

```jsx
const a = Number('lightix');
console.log(a, typeof a); // NaN 'number'

const b = Number('28');
console.log(b, typeof b); // 28 'number'
```

### String

글자와 기타 문자들을 다루기 위한 데이터 타입이다.

- 문자열 데이터 타입은 따옴표 쌍으로 둘러싸여 있다
- 타 언어와 달리 한글자든 여러글자든 모두 string type

```jsx
const char = 'c';
const lightix = 'lighix';
const greeting = 'hello' + lightix; // string + 변수 도 가능하다
```

### Boolean

true 혹은 fasle 중 하나의 값만 가질 수 있는 데이터 타입이다.

- 참 (true) : 거짓을 뺀 모든 값
- 거짓 (false) : 0, null, undefined, NaN, ' '

```jsx
const canRead = true;
const test = 3 < 1; //false
```

### Null /  Undefined

- null 은 '값이 비어있다' 는 object 타입이다.
- undefined 는 선언은 되어 있지만, 값이 있는지 비었는지 정해지지 않은 상태

```jsx
let nothing = null; // null
let x; // undefined

console.log(nothing == x); // true
console.log(nothing === x); // false
```

### Object

일상생활에서 볼 수 있는 물건을 대표하는 박스 형태

```jsx
const lightix = { name : '이기웅', age: 20 };
// const로 정의되었어도 레퍼런스가 잠긴거라 안에있는 name과 age 변수는 다른 값으로 할당이 가능하다.
// 오브젝트가 가르키는 레퍼런스가 저장된다
```

### Function

프로그램을 구성하는 가장 기본적인 빌딩 블록으로 한가지의 일을 수행하거나 값을 계산할 때 사용한다

```jsx
function printHello() {
	console.log('Hello');
}
printHello();
```

### Symbol

고유한 식별자를 만들 때 사용하는 데이터 타입으로 ES6부터 등장했다. 

```jsx
const symbol1 = Symbol('lightix');
const symbol2 = Symbol('lightix');
console.log(symbol1 === symbol2); // 같은 문자열을 넣었어도 고유한 식별자로 사용되기 때문에 false

// 문자열이 같으면 동일한 심볼을 만들고 싶을 때는
const gSymbol1 = Symbol.for('lightix');
const gSymbol2 = Symbol.for('lightix'); 
console.log(gSymbol1 === gSymbol2); // true

// symbol을 바로 출력하고 싶을 때는
console.log(symbol1.description); // .description 을 붙여서 string으로 변환해야 한다
```
<br />

## Variable & Constant (변수와 상수)

변수(Variable)란, 값을 저장할 수 있는 메모리의 공간을 의미한다.

상수(Constant)란, 값을 한 번 저장하면 변경할 수 없는 값이다.

### let (변수)

- Mutable type / read & write
- IE에서는 지원하지 않는다
- block-scope
- 재선언은 Error!

```jsx
let name = 'lightix';
let name = '이기웅'; // Error
name = '이기웅'; // Ok
```

### Const (상수)

- Immutable type / read only
- 변경이 되지 않기 때문에 보안상 안전하다
- 한 번 할당한 이후로는 변경되지 않는 데이터 타입이기 때문에 선언과 동시에 값을 할당해야 한다
- block-scope

```jsx
const name = 'lightix';
name = '이기웅'; // Error

const d = { test: 20 };
d.test = 30; // Ok
```

**Q. 왜 객체는 const로 정의해도 값의 변경이 가능할까 ?**

> number, string, boolean, null, undefined 는 primitive 타입으로 값 자체가 레퍼런스에 저장된다. 반면에 객체는 레퍼런스가 const로 정의되었기 때문에 변경이 불가능 하지만, 레퍼런스가 가르키고 있는 값들은 변경이 가능하다

### var

- function-scope (block-scope 무시)
- 값을 선언하기도 전에 호출할 수 있다 (호이스팅)

    호이스팅 : 어디에 선언했는지 상관없이 항상 제일 위로 선언을 끌어 올려주는 것

```jsx
var a = 10;
a = 20; // OK
```

### Scope

변수를 사용할 수 있는 코드는 변수가 선언된 위치에 따라 달라진다. 만일 변수를 함수 내에 선언했으면 그 변수는 함수 내에서만 사용할 수 있다. 이렇게 변수가 사용 가능한 영역(참조 범위)을 변수의 범위(scope)라고 한다.

- 전역 Scope (Global scope) : 코드 어디에서든지 참조할 수 있다
- 지역 Scope (Local scope) : 정의된 함수 내에서만 참조할 수 있다
- 블록 Scope (Block scope) : if, for, switch 등 특정 블록 내부에서만 참조할 수 있다.

전역 변수는 항상 메모리에 저장되기 때문에 최소한으로 사용하는 것이 좋다

```jsx
let globalName = 'global name';
{
	let name = 'lightix';
	console.log(globalName); // 전역변수이기 때문에 안에서 접근이 가능하다
}

console.log(name); // 지역변수이기 때문에 밖에서 접근이 불가능하다
console.log(globalName); // 전역변수이기 때문에 밖에서 접근이 가능하다
```

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

function scope가 block scope를 포함한다.

`let`은 block이든 function이든 내부에 선언된 값이 밖으로 나오지 않는다.

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

`const` 로 선언된 Block Scope로 선언된다. 따라서, if문 같은 블록 내에서 변수/상수를 선언하면, 해당 블록 내부에서만 사용이 가능하며, 블록 밖의 범위에서 똑같은 이름을 가진 값이 있다고 해도, 영향을 주지 않는다.

`let` 도 마찬가지 !

하지만 `var`는 다르다

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

### Hoisting

Hoisting이란, 자바스크립트에서 아직 선언되지 않은 함수/변수를 '끌어 올려서' 사용할 수 있는 자바스크립트의 작동 방식을 의미한다.

```jsx
myFunction();

function myFunction() {
	console.log('hello world');
}
```

`myFunction` 함수를 선언하기 전에, `myFunction()` 을 호출했다. 함수가 선언되지 않았음에도 코드는 에러없이 작동된다. 위 코드를 자바스크립트 엔진이 해석하는 과정에서 다음과 같이 받아들인다.

```jsx
function myFunction() {
	console.log('hello world');
}

myFunction();
```

이런 현상을 Hoisting이라고 부른다. 함수 뿐 아니라 변수도 Hoisting이 된다.

```jsx
console.log(num); // Error
```

`num`은 정의되지 않았다고 오류가 발생한다.

```jsx
console.log(num); // undefined
var num = 1;
```

위 코드를 자바스크립트 엔진이 해석하는 과정에서 다음과 같이 받아들인다.

```jsx
var num;
console.log(num); // undefined
num = 1;
```

`const`, `let`도 똑같이 변수 사전에 들어가서 호이스팅이 된다.

```jsx
const num = add(10, 20);

console.log(num); // 30

function add(a, b) {
	return a + b;
}
```

단, `var`랑은 다르게 코드를 선언하는 구문에 도달하기 전에는 변수를 사용할 수 없도록 하는 기능이 추가됐다. 선언돼서 초기화 되기 전까지는 TDZ(Temporal Dead Zone)영역에 속하게 된다

```jsx
const hello = 100;

function print1() {
	console.log(hello); // 100
}

function print2() {
	console.log(hello); // Error
	const hello = 200;
}
```
<br />



<br />


### Closure

생성한 시점의 scope chain을 계속 갖고 있는 것을 말한다

아직 이해가 되지 않으니 여기 저기 검색 후 수정하자!!!

```jsx
var c = 'X';

function outer() {
	var a = 1;
	var b = 'B';

	function inner() {
		var a = 2;
		console.log(c);
	}
	return inner;
}
var someFun = outer();
someFun(); // 'X'
```

- `outer` 함수는 `inner` 함수를 리턴하고, `inner` 함수는 `b`를 출력한다. `someFun` 함수는 `outer`함수(return된 inner)를 받는다. 이때 클로저 때문에 `outer`함수가 실행된 다음에도 `someFun` 함수에도 `outer` 함수의 scope에 계속 접근할 수 있다.
- inner 함수가 outer 함수가 갖고있는 변수도 갖고 있게 된다.

```jsx
var btns = [
	document.getElementById('btn0'),
	document.getElementById('btn1'),
	document.getElementById('btn2')
];

function setClick() {
	for(var i = 0; i < 3; i++) {
		btn[i].onclick = function() {
			console.log(i);
		}
	}
}
setClick();
```

- 먼저, global scope가 하나 생성된다
- global scope 안에는 btns와 setClick이 들어간다
- 그리고 setClick이 실행될 때, setClick함수를 위한 스코프가 생성된다
- setClick함수의 스코프에는 변수 i 가 들어간다 (실제로는 this도 들어간다)
- for 문이 실행되면서 변수 i는 최종적으로 3이 돼서 반복을 종료한다
- i가 3이 됐기 때문에 어떤 버튼을 클릭하든 console에는 3이 출력된다

```jsx
var btns = [
	document.getElementById('btn0'),
	document.getElementById('btn1'),
	document.getElementById('btn2')
];

function setClick() {
	for(let i = 0; i < 3; i++) {
		btn[i].onclick = function() {
			console.log(i);
		}
	}
}
setClick();
```

- let으로 선언됐을 경우 for문의 중괄호도 스코프 생성이 되기 때문에 각각의 값을 저장한다.
- let이 for문에서만 특이하다 ?
