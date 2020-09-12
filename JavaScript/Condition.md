# Condition (조건문)
특정 조건에 따라 코드가 실행되게 하는 구문
<br />
<br />
## if..else (조건문)
주어진 조건 식의 결과에 따라 코드 블럭의 실행을 결정한다. 조건식은 불리언 값으로 평가될 수 있는 표현식이다.

`if(조건) { 조건이 true일 때 실행할 코드}`

```jsx
const name = 'df';
if (name === 'lightix') {
	console.log('Welcome, Lightix!');
} else if (name === 'coder') {
	console.log('Welcome, coder');
} else {
	console.log('unknown');
}
```


만약 코드 블록 내의 문이 하나면 중괄호를 생략해도 된다.
```jsx
const name = 'df';
if (name === 'lightix') console.log('Welcome, Lightix!');
else if (name === 'coder') console.log('Welcome, coder');
else console.log('unknown');
```

<br />

## Ternary operator (삼항 연산자)

`조건 ? true일 때 값 : false일 때 값;`

- 간단한 값으로 귀결될 때에만 사용하는 것이 좋다

```jsx
const name = 'df';

console.log(name === 'lightix' ? 'yes' : 'no'); // no
```

<br />

## Switch statement (조건문)
switch 문은 switch 문의 표현식을 평가해서 그 값과 일치하는 표현식을 갖는 case 문으로 이동한다. case문은 상황을 의미하는 표현식을 지정한다. switch문의 표현식과 일치하는 case 문이 없으면 default 문을 실행한다.

`switch (표현식) { case 표현식1 : 할 일; case 표현식2 : 할 일; default : 할 일;}` 

- `if`, `else if` 가 여러번 반복된다면 switch문을 사용하는 것이 좋다.
- `if..else` 문의 조건식은 반드시 불리언으로 귀결되지만, switch 문의 표현식은 문자열이나 숫자 값인 경우가 많다. switch 문은 논리적 참,거짓보다는 다양한 상황에 따라 달라질 때 사용한다.
- 타입스크립트에서 정해져 있는 타입을 검사할 때 사용하는 것이 가독성에 좋다.

```jsx
const browser = 'IE';

switch (browser) {
	case 'IE':
		console.log('Go away!');
		break;
	case 'Chrome':
	case 'Firefox':
		console.log('love you!');
		break;
	default:
		console.log('same all!');
		break;
}
```
만약, `break`문이 없다면 `case`문의 표현식과 일치하지 않더라도 실행 순서는 다음 `case`로 이동해서 결국 `default`문을 실행한다. 
```jsx
const browser = 'IE';

switch (browser) {
	case 'IE':
		console.log('Go away!');
	case 'Chrome':
	case 'Firefox':
		console.log('love you!');
	default:
		console.log('same all!');
}
```

`switch`문의 표현식의 평가 결과와 일치하는 `case`문으로 이동해서 `console.log('Go away!')`를 실행한 것은 맞지만, 문을 실행한 후 `switch` 문을 탈출하지 않고 `switch`문이 끝날 때까지 모든 `case`,`default`를 실행한다.

단, `default` 문은 가장 마지막에 위치하므로 `break`문을 생략하는 것이 일반적이다. 