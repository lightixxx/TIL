# Condition (조건문)
특정 조건에 따라 코드가 실행되게 하는 구문
<br />
<br />
### if, else if, else (조건문)

`if(조건) { 조건이 true일 때 실행할 코드}`

조건에 따라 코드를 실행한다

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
<br />
### Ternary operator (삼항 연산자)

`조건 ? true일 때 값 : false일 때 값;`

- 간단한 값으로 귀결될 때에만 사용하는 것이 좋다

```jsx
const name = 'df';

console.log(name === 'lightix' ? 'yes' : 'no'); // no
```
<br />
### Switch statement (조건문)

`switch (검사할 변수) { case 조건 : 할 일; case 조건 : 할 일; default : 할 일;}` 

- if, else if 가 여러번 반복된다면 switch문을 사용하는 것이 좋다
- 타입스크립트에서 정해져 있는 타입을 검사할 때 사용하는 것이 가독성에 좋다

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
