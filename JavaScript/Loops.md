# Loops (반복문)
프로그래머가 중요한 덕목 중 하나는 불필요한 코드를 줄이는 것이다.

반복문을 이용하면 불필요하게 반복된 코드를 줄일 수 있다.

<br />

## for
조건식이 거짓이 될 때까지 코드 블록을 반복해서 실행한다.

`for(begin; condition; step)`

- for (초기화; 반복 조건; 반복이 된 후 실행되는 코드) { 반복이 되는 코드 블럭 }

```jsx
for (let i = 0; i < 5; i++) {
	console.log(i); // 0, 1, 2, 3, 4
}
```
1. for 문이 실행되면 단 한번만 초기화식 `let i = 0`이 실행된다.
2. 초기화식의 실행이 종료되면 조건식으로 이동해서 참인지 거짓인지 판단한다.
3. 조건식의 평가 결과가 `true` 이므로 코드 블록으로 이동해서 실행한다.
4. 코드 블록이 실행된 이후 증감식으로 이동해서 `i++`가 실행되어 `i = 1`이 된다.
5. 증감식 실행된 이후에 다시 조건식을 확인한다.
6. 조건식의 결과가 `true` 이므로 코드 블록을 실행한다.
7. 2번에서 5번까지 계속 반복된다.
8. 조건식의 결과가 `false`가 되면 for문의 실행이 종료된다.

<br />

## nested loops (중첩 반복문)

`for`문 안에 `for`문이 중첩된 형태이다.

- O(2**n)는 cpu에 많은 메모리를 차지하므로 지양하는 것이 좋다
- 중첩된 반복문은 코드의 가독성이 떨어지므로 지양하는 것이 좋다

```jsx
for (let i = 0; i < 10; i++) {
	for (let j = 0; j < 10; j++) {
		console.log(`i: ${i}, j:${j}`);
	}
}
// i가 0이고 i 가 10보다 작으니까 j를 0-9까지 반복하고 i++ 해라
// i가 1이고 i 가 10보다 작으니까 j를 0-9까지 반복하고 i++ 해라
// i가 2이고 i 가 10보다 작으니까 j를 0-9까지 반복하고 i++ 해라
// ...
// i가 9이고 i 가 10보다 작으니까 j를 0-9까지 반복하고 i++ 해라
```

<br />

## break, continue

- break: loop를 끝낼 때 사용한다
- continue: loop 중 지금 것만 스킵하고 다음 loop 실행한다. break처럼 반복문을 탈출하지는 않는다.

```jsx
//Quiz
// 1. 0부터 10까지의 숫자 중 짝수만 출력하기 (continue 사용)
for(let i = 0; i <= 10; i++ ) {
  if(i % 2 !== 0) {
    continue;
  }
  console.log(i);
}

// 2. 0부터 10까지의 숫자를 출력하다가 8이되면 그만하기 (break 사용)
for(let i = 0; i <= 10; i++) {
  console.log(i);
  if(i > 8) {
    break;
  }
}
```

<br />

## while

- 조건이 거짓이 될 때까지 실행한다

```jsx
let i = 3;
while (i > 0) {
	console.log(`while: ${i}`); // 3, 2, 1
	i--;
}
```
<br />

## do while

- 무조건 한 번 코드 블럭을 실행한 다음에 조건이 맞는지 아닌지 검사한다
- 블럭을 먼저 실행하고 싶은 경우에 사용한다.

```jsx
let i = 3;
do {
	console.log(`do while: ${i}`); // 3, 2, 1
	i--;
} while (i > 0);
```

<br />

## forEach

`forEach` 반복문은 배열에서 사용가능한 메서드이다. 배열의 요소를 반복하여 작업할 수 있다.

```jsx
const items = ['lightix', 'kiwoong', 'Mrlee'];
items.forEach(function(item) {
	console.log(item); // 'lightix', 'kiwoong', 'Mrlee'
}); 
```

<br />

## for ...of

`for of` 반복문은 ES6에 추가된 반복구문이다. 

```jsx
for(const i of [1, 2, 3]) {
	console.log(i); // 1, 2, 3
}
```

<br />

## for ...in

`for in` 반복문은 객체의 속성들을 반복해서 작업을 수행할 수 있다. 단, 객체의 key 값에 접근할 수 있지만, value 값에 접근하는 방법은 없다.

```jsx
const obj = {
	a: 1,
	b: 2,
	c: 3
};

for(const i in obj) {
	console.log(i, obj[i]); // a 1, b 2, c 3
}
```
