# closure (클로저)

p.142 정리

생성한 시점의 scope chain을 계속 갖고 있는 것을 말한다

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

##### `outer` 함수는 `inner` 함수를 리턴하고, `inner` 함수는 `b`를 출력한다. `someFun` 함수는 `outer`함수(return된 inner)를 받는다. 이때 클로저 때문에 `outer`함수가 실행된 다음에도 `someFun` 함수에도 `outer` 함수의 scope에 계속 접근할 수 있다. `inner` 함수가 `outer` 함수가 갖고 있는 변수도 갖고 있게 된다.

<br />

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

- 먼저, global scope가 하나 생성된다.
- global scope 안에는 btns와 setClick이 들어간다.
- 그리고 setClick이 실행될 때, setClick함수를 위한 스코프가 생성된다.
- setClick함수의 스코프에는 변수 i 가 들어간다 (실제로는 this도 들어간다).
- for 문이 실행되면서 변수 i는 최종적으로 3이 돼서 반복을 종료한다.
- i가 3이 됐기 때문에 어떤 버튼을 클릭하든 console에는 3이 출력된다.

<br />

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
