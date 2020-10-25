# Basic Syntax

- 자바스크립트의 기본 문법 및 개념을 정리한 파일입니다.
- 비전공 프론트엔드 입문자가 이해한 만큼 작성했습니다.

<br />

## 📌 여기서 꼭 알아야 할 개념
- Expression (표현식) : 값을 만들어내는 간단한 코드
- Statement (문장) : 하나 혹은 여러 개의 표현식이 모여 구성되는 코드를 읽어들이는 단위가 되는 것
- Keyword (키워드) : 프로그래밍 언어가 처음 만들어질 때 정해진 특별한 의미가 있는 단어
- Identifier (식별자) : 이름을 붙일 때 사용하는 단어
- Comments (주석) : 프로그램 코드를 설명하며, 프로그램의 진행에 전혀 영향을 주지 않는 문장
- String (문자열) : 문자를 표현할 때 사용하는 자료형
- Number (숫자) : 숫자를 표현할 때 사용하는 자료형
- Boolean (불,불리언) : 참과 거짓을 표현할 때 사용하는 자료형
- Variable (변수) : 값을 저장할 때 사용하는 식별자

<br>

## Expression
값을 만들어내는 간단한 코드를 표현식이라고 한다. 리터럴, 식별자, 연산자, 함수 호출 등의 조합을 말한다. 표현식은 실행하여 하나의 값을 만드는 과정을 통해 값을 만든다. 즉, 표현식은 하나의 값으로 귀결되는 문(statement)이다.

```jsx
// 리터럴 표현식
20
// 식별자 표현식
sum
// 연산자 표현식
100 + 20 + 3
// 함수/메소드 호출 표현식
square()
```

표현식은 결국 하나의 값으로 귀결되므로 표현식과 값은 동등한 관계이기 때문에 값처럼 사용할 수 있다. 즉, 값이 위치할 수 있는 자리에는 표현식도 위치할 수 있다는 의미이다.

##### 표현식은 값을 만들어내기 때문에 함수의 인자로 사용할 수 있다.

```jsx
console.log(100 + 20 + 3);
alert("Hello" + " World");
```
<br />

## Statement
하나 혹은 여러 개의 표현식이 모여서 문장을 이룬다. 문이 실행되면 무슨일인가 일어난다. 변수 선언문을 실행하면 변수가 선언되고, 할당문을 실행하면 할당이 된다.
```jsx
// 변수 선언문
var x;
// 할당문
x = 5;
// 함수 선언문
function foo() {...}
// 조건문
if (x > 5) {...}
// 반복문
for (var i = 0; i < 10; i ++) {...}
```
- 모든 표현식은 문장이 될 수 있다.
- 보통 문장의 끝에는 세미 콜론을 붙인다.

```jsx
const name = "lightix";
alert(name);
true; 20; 100+20+3 // 123
```

- 한 줄에 문장이 하나인 경우에는 세미 콜론을 붙이지 않아도 문제가 없지만 관례적으로 붙인다.
- 한 줄에 여러 문장을 적을 경우, 세미 콜론으로 문장을 구분해야 한다.
- 마지막 문장을 세미 콜론을 붙이지 않아도 문제가 없다.
- 여러 문장을 썼을 때, 마지막 문장의 결과가 반환된다.

<br />

> 표현식과 문은 유사해서 구별이 어려울 수 있다. 표현식은 값으로 귀결되지만 그 이상의 행위는 할 수 없다. 문은 선언 키워드를 사용해서 변수나 함성을 생성하기도 하고, 제어문을 생성하여 프로그램의 흐름을 제어하기도 한다.
> 
> 표현식의 역할은 값을 생성하는 것이다. 문의 역할은 표현식으로 생성한 값을 사용해 컴퓨터에게 명령을 내리는 것이다. 문에는 표현식인 문과 표현식이 아닌 문이 있다. 예를 들어 선언문은 값으로 평가될 수 없다. 따라서 표현식이 아닌 문이다. 하지만 할당문은 그 자체가 표현식인 문이다.

```jsx
// 선언문
var x = 5 * 10; // 표현식 x = 5 * 10을 포함하는 문이다.

// 할당문
x = 100; // 이 자체가 표현식이지만 완전한 문이기도 하다.
```
위 예제의 선언문은 표현식이 아닌 문이다. 다시 말해 값으로 귀결될 수 없다. 따라서 선언문은 값처럼 사용할 수 없다.

이에 반해 할당문은 그 자체가 표현식이다. 다시 말해 할당문은 표현식인 문이다.

> 개발자도구에서 표현식이 아닌 문은 언제나 undefined를 반환하고,표현식인 문은 언제나 값을 반환한다.

<br />

### **📌 표현식이 모여서 문장이 되고, 문장들이 모여서 프로그램이 된다**

<br />

## Keywords & Reserved Words

### Keywords

자바스크립트에서 특정한 목적을 위해 사용하는 단어로 이러한 키워드들은 예약어로 지정되어 있다.

```jsx
const name = 'lightix' // const 라는 단어는 상수를 선언할 때 사용하는 키워드
```

<br />

### Reserved Words

프로그램을 작성할 때, 변수명, 함수명 등 이름으로 사용할 수 없는 단어.

```jsx
let return = 'lightix'; // return 은 예약어이기 때문에 변수명으로 사용할 수 없다
function for() {} // for 은 예약어이기 때문에 함수명으로 사용할 수 없다
```

<br />

### Reserved keywords

이미 특정한 목적을 위해 사용하기 때문에 사용할 수 없는 예약어. (런타임 환경마다 다를 수 있음)

[MDN- Reserved keywords](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Lexical_grammar#%ED%82%A4%EC%9B%8C%EB%93%9C)

<br />

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

📌 프로그램에서 사용하는 변수나 함수의 이름을 짓는 것은 언제나 어려운 일이다.

📌 의미없는 이름은 사용하지 않고, 역할에 맞는 적절한 이름을 짓도록 노력해야 한다.

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
<br />

### 자바스크립트는 크게 두 가지 데이터 타입을 갖는다

1. Primitive data type : Number, String, Boolean 등과 같이 값이 전달되는 타입
   * 변경 불가능한 값(immutable value)
   * 값에 의한 전달(pass-by-value)
2. Reference data type : Array, Object, Function 과 같이 참조로 전달되며, 포인터 주소만 복사하고 동일한 데이터를 모두 공유하는 타입
<br />

### Variable types

- 더이상 작은 단위로 나누어지지 않는 단일 아이템 : number, string, boolean, null, undefined, symbol
- 단일 아이템을 여러개 묶어서 한 박스로 관리할 수 있는 아이템 : object
- 함수는 1급 객체이다

<br />

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

<br />

### String

글자와 기타 문자들을 다루기 위한 데이터 타입이다.

- 문자열 데이터 타입은 따옴표 쌍으로 둘러싸여 있다
- 타 언어와 달리 한글자든 여러글자든 모두 string type

```jsx
const char = 'c';
const lightix = 'lighix';
const greeting = 'hello' + lightix; // string + 변수 도 가능하다
```
문자열은 배열처럼 인덱스를 통해 접근이 가능하다.(유사 배열)
```jsx
const str = 'lightix';
for(let i = 0; i < str.length; i++) {
	console.log(str[i]);
}

// 단, 변경할 수는 없다
str[3] = 'x';
console.log(str); // lightix
```
한 번 생성된 문자열은 read only로 변경이 불가능(immutable)하다.

<br />

### Boolean

true 혹은 fasle 중 하나의 값만 가질 수 있는 데이터 타입이다.

- 참 (true) : 거짓을 뺀 모든 값
- 거짓 (false) : 0, null, undefined, NaN, ' '은 false로 간주.

```jsx
const canRead = true;
const test = 3 < 1; //false
```

<br />

### Null /  Undefined

- null 은 개발자가 명시적으로 '값이 비어있다' 는 상태를 나타낼 때 사용한다.
  * typeof의 결과는 object, 값은 null 이다.
- undefined 는 선언은 되어 있지만, 값이 있는지 비었는지 정해지지 않은 경우를 표현할 때 사용한다.
	* 선언만 하고 초기화하지 않은 변수의 타입이나 값.
	* 객체의 정의되지 않은 속성의 타입이나 값.
```jsx
let nothing = null; // null
let x; // undefined

console.log(nothing == x); // true
console.log(nothing === x); // false
```

<br />

### Object
데이터와 그 데이터에 관련한 동작을 모두 포함하는 개념적인 존재이다. 이름과 값을 갖는 데이터를 의미하는 프로퍼티(property)와 동작을 의미하는 메소드(method)를 포함할 수 있는 독립적 주체를 말한다.
- Primitives 를 제외한 모든 것
- 일상생활에서 볼 수 있는 물건을 대표하는 박스 형태
- 참조에 의한 전달방식(pass-by-reference)으로 전달된다.
```jsx
const lightix = { name : '이기웅', age: 20 };
```

<br />

### Function

프로그램을 구성하는 가장 기본적인 빌딩 블록으로 한 가지의 일을 수행하거나 값을 계산할 때 사용한다

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

변수(Variable)란, 프로그램에서 사용되는 데이터를 일정 기간 동안 기억하여 필요한 때에 다시 사용하기 위해 데이터에 고유의 이름인 식별자(identifier)를 명시한 것이다. 값을 저장할 수 있는 메모리의 공간을 의미한다.

상수(Constant)란, 값을 한 번 저장하면 변경할 수 없는 값이다.
```jsx
let score; // 변수 선언
score = 80; // 값의 할당
score = 90; // 값의 재할당
score; // 변수의 참조
```


<br>

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
<br>

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


<br>

### var

- function-scope (block-scope 무시)
- 값을 선언하기도 전에 호출할 수 있다 (호이스팅)

    호이스팅 : 어디에 선언했는지 상관없이 항상 제일 위로 선언을 끌어 올려주는 것

```jsx
var a = 10;
a = 20; // OK
```
<br>

## scope
스코프는 식별자를 찾아내기 위한 규칙이다. 변수를 사용할 수 있는 코드는 변수가 선언된 위치에 따라 달라진다. 만일 변수를 함수 내에 선언했으면 그 변수는 함수 내에서만 사용할 수 있다. 이렇게 변수가 사용 가능한 영역(참조 범위)을 변수의 범위(scope)라고 한다.
자세한 내용은 [scope](https://github.com/lightixxx/TIL/blob/master/JavaScript/learnMore/scope.md) 에 정리하자.

<br />

## hoisting
호이스팅은 Hoisting이란, 자바스크립트에서 아직 선언되지 않은 함수/변수를 '끌어 올려서' 사용할 수 있는 자바스크립트의 작동 방식을 의미한다. 자세한 내용은 [hoisting](https://github.com/lightixxx/TIL/blob/master/JavaScript/learnMore/hoisting.md) 에 정리하자.


<br />

## Closure
뭔가 굉장히 복잡한 개념인 듯 보인다. 추후에 [closure]([https://](https://github.com/lightixxx/TIL/blob/master/JavaScript/learnMore/closure.md)) 에 정리하자.

<br />

##### 출처

- [Poiema Web](https://poiemaweb.com/js-data-type-variable)
- [Dream Coding Ellie](https://youtu.be/OCCpGh4ujb8)