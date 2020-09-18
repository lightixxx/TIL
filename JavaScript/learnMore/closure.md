# closure (클로저)
자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우, 외부 함수 밖에서 내부함수가 호출되더라도 외부함수의 지역 변수에 접근할 수 있는 함수를 클로저라고 부른다. 즉, 반환된 내부함수가 자신이 선언됐을 시점의 스코프(Lexical Scope)를 기억해서 자신이 선언됐을 때의 스코프 밖에서 호출되어도, 그 스코프에 접근할 수 있는 함수를 말한다.

생성한 시점의 scope chain을 계속 갖고 있는 함수를 말한다.

```jsx
function test(name) {
	var output = `Hello, ${name}!`;
}

console.log(output);
```
위 코드는 오류가 있다. `test()`함수 안에 선언된 변수 `output`은 지역 변수이므로 함수 외부에서 사용할 수 없다. 지역 변수는 함수가 실행될 때 생성되고, 함수가 종료될 때 사라지기 때문이다. 

하지만 클로저를 사용하면 가능케 할 수 있다.
```jsx
function test(name) {
	var output = `Hello, ${name}!`;
	return function() {
		console.log(output);
	};
}

test('lightix')();
```
위 코드에서 지역 변수 `output`은 `test()` 함수를 호출할 때 생성된다.
변수 `output`은 지역 변수 이기 때문에, 함수가 종료될 때 사라져야 한다. 하지만 해당 변수가 이후에도 활용될 가능성이 있기 때문에 자바스크립트는 변수를 제거하지 않고 남겨둔다. 

즉, 외부함수가 이미 반환이 됐어도 외부함수 내의 변수는 이를 필요로 하는 내부함수가 하나 이상 존재하는 경우 계속 유지된다. 이때 내부함수가 외부함수에 있는 변수의 복사본이 아니라 실제 변수에 접근하는 것이다.

추가로 지역 변수 output을 남겨둔다고 외부에서 마음대로 사용할 수 있는 것은 아니다. 꼭 리턴된 클로저 함수를 사용해야 지역 변수 `output`을 사용할 수 있다. 

```jsx
function test(name) {
	var output = `Hello, ${name}!`;
	return function() {
		console.log(output);
	};
}

var test_1 = test('lightix');
var test_2 = test('lvvrvsh');

test_1(); // Hello, lightix!
test_2(); // Hello, lvvrvsh!
```
위 코드에서 볼 수 있듯이 클로저 함수로 인해 남은 지역 변수는 클로저 함수 각각의 고유한 변수이다.

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
`outer` 함수는 `inner` 함수를 리턴하고, `inner` 함수는 `b`를 출력한다. `someFun` 함수는 `outer`함수(return된 inner)를 받는다. 이때 클로저 때문에 `outer`함수가 실행된 다음에도 `someFun` 함수에도 `outer` 함수의 scope에 계속 접근할 수 있다. `inner` 함수가 `outer` 함수가 갖고 있는 변수도 갖고 있게 된다.

<br />

## 클로저의 활용
클로저가 가장 유용하게 사용되는 상황은 현재 상태를 기억하고 변경된 최신 상태를 유지하는 것이다. 변수를 기억하고 상태가 변경되어도 최신 상태를 유지해야하는 상황에 매우 유용하다. 클로저가 없다면 전역변수를 사용해야 하는데, 전역변수는 최대한 지양하는 것이 좋으므로 사용을 억제해야한다.

이론만 주구장창하지 말고 코드를 짜보고.. 그때 정리하도록 하자...

[출처 - poiemaweb](https://poiemaweb.com/js-closu)