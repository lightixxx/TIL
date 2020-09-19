# Math 객체
수학 상수와 함수를 위한 프로퍼티와 메서드를 제공하는 빌트인 객체이다. 자바스크립트의 기본 내장 객체 중 유일하게 생성자 함수를 사용하지 않는 객체이다. 따라서 정적 프로퍼티와 메서드만 제공한다.

<br />

## Math property

<br />

### Math.PI
PI 값(π ≈ 3.141592653589793)을 리턴한다.
```jsx
Math.PI; // 3.141592653589793
```
<br />

### Etc
평생 쓸 일 없을 것 같지만 정리..
|Property Name|Value|
|--------|--------|
|E|2.718281828459045|
|LN2|0.6931471805599453|
|LN10|2.302585092994046|
|LOG2E|1.4426950408889633|
|LOG10E|0.4342944819032518|
|SQRT1_2|0.7071067811865476|
|SQRT2|1.4142135623730951|

<br />
<br />

## Math Method
Math 객체의 메서드로 넘겨진 모든 매개변수는 종류에 관계없이 모두 숫자로 변환한다.

<br />

### Math.abs(x)
x의 절댓값(0 또는 양수)을 리턴한다.
```jsx
Math.abs(-1); // 1
Math.abs('1'); // 1
Math.abs(''); // 0
Math.abs(null); // 0
Math.abs(undefined); // NaN
Math.abs('lightix'); // NaN
```

### Math.round(x)
인수를 반올림해서 정수를 리턴한다.
```jsx
Math.round(1.234); // 1
Math.round(-1.234); // -1
Math.round(1.678); // 2
Math.round(-1.678); // -2
```

### Math.ceil(x)
인수를 올림해서 정수를 리턴한다.
```jsx
Math.ceil(1.3); // 2
Math.ceil(-1.3); // -1
Math.ceil(1.8); // 2
Math.ceil(-1.8); // -1
```

### Math.floor(x)
인수를 내림해서 정수를 리턴한다.
- 인수보다 작거나 같은 가장 큰 정수를 리턴한다.
- 음수는 소수점 이하를 떼어 버린 다음 -1을 한 정수를 리턴한다.
```jsx
Math.floor(2.9); // 2
Math.floor(-2.9); // -3
Math.floor(6.1); // 6
Math.floor(-6.1); // -7
```

### Math.sqrt(x)
인수의 제곱근을 리턴한다.
```jsx
Math.sqrt(9); // 3
Math.sqrt(-9); // NaN
Math.sqrt(3); // 1.7320508075688772
```

### Math.random()
0부터 1까지의 임의의 수를 리턴한다.
```jsx
Math.random();
```

하도 이론 공부만 하느라 지겨워서 만들어 본 로또 추첨기
```jsx
// 로또 번호 추첨
// 중복된 값이 나올 경우 재추첨 할 것
// 순서대로 정렬할 것
function lottoMachine() {
  const winningNum = [];

  for(let i = 0; i < 6; i++) {
    let lotto = Math.floor((Math.random() * 45) + 1);
    if(! sameNum(lotto)) {
      winningNum.push(lotto);
    } else {
      i--
    }
  }

  function sameNum(lotto) {
    return winningNum.find((e) => (e === lotto));
  }

  return winningNum.sort(function(a, b) {
    return a - b;
  });
}

lottoMachine();
```
`Math.random()`을 단순히 6번 반복하면 로또 번호 추첨기 만들겠는데 싶었지만, 어림도 없네..

- 순서가 지 멋대로 나와서 `sort()`했는데, 1, 23, 3, 42, 5, 8  이런식으로 나와서 1차 당황.
- 중복된 값이 나와서 2차 당황.

어찌 저찌 중복도 없고, 순서대로 정렬도 되긴 하지만 뭔가 요상한 코드..

`return`문 안에 `return`을 써도 되는걸까..

### Math.max(x, y, z ... n)
인수 중에서 가장 큰 수를 리턴한다. 
```jsx
Math.max(1, 2, 3); // 3
```

### Math.min(x, y, z ... n)
인수 중에서 가장 작은 수를 리턴한다.
```jsx
Math.min(1, 2, 3); // 1
```