# hoisting
Hoisting이란, 자바스크립트에서 아직 선언되지 않은 함수/변수를 '끌어 올려서' 사용할 수 있는 자바스크립트의 작동 방식을 의미한다.

```jsx
myFunction();

function myFunction() {
	console.log('hello world');
}
```
`myFunction` 함수를 선언하기 전에, `myFunction()` 을 호출했다. 함수가 선언되지 않았음에도 코드는 에러없이 작동된다. 위 코드를 자바스크립트 엔진이 해석하는 과정에서 다음과 같이 받아들인다.

<br />

```jsx
function myFunction() {
	console.log('hello world');
}

myFunction();
```
이런 현상을 Hoisting이라고 부른다. 함수 뿐 아니라 변수도 Hoisting이 된다.

<br />

#### 변수는 3단계에 걸쳐 생성된다.
1. 선언 단계 (Declaration phase)
   * 변수 객체에 변수를 등록한다.
   * 이 변수 객체는 스코프가 참조하는 대상이 된다. 	
2. 초기화 단계 (Initialization phase)
   * 변수 객체에 등록된 변수를 메모리에 할당한다.
   * 이 단계에서 변수는 `undefined`로 초기화된다
3. 할당 간계 (Assignment phase)
   * `undefined`로 초기화된 변수에 실제값을 할당한다.

<br />


```jsx
console.log(num); // Error
```

`num`은 정의되지 않았다고 오류가 발생한다.

```jsx
console.log(num); // undefined
var num = 1;
```
위 코드를 자바스크립트 엔진이 해석하는 과정에서 다음과 같이 받아들인다.

<br />

```jsx
var num;
console.log(num); // undefined
num = 1;
```
`const`, `let`도 똑같이 변수 사전에 들어가서 호이스팅이 된다.

<br />

```jsx
const num = add(10, 20);

console.log(num); // 30

function add(a, b) {
	return a + b;
}
```
단, `var`랑은 다르게 코드를 선언하는 구문에 도달하기 전에는 변수를 사용할 수 없도록 하는 기능이 추가됐다. 선언돼서 초기화 되기 전까지는 TDZ(Temporal Dead Zone)영역에 속하게 된다

<br />

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