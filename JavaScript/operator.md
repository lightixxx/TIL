# Operator (연산자)
연산자는 하나 혹은 그 이상의 값을 하나의 값으로 만들 때 사용한다.
자바스크립트의 연산자는 할당, 비교, 산술, 비트, 논리, 문자열, 조건, 쉼표, 단항, 관계 등 다양한 연산자가 있다.

<br />

## 대입 연산자 or 할당 연산자
오른쪽 피연산자의 값을 왼쪽 피연산자에 할당한다.

<br />

### 할당 연산자
기본적으로 오른쪽의 피연산자 값을 왼쪽 피연산자 값에 할당하는 등호 `=` 로 할당한다.
```jsx
const color = blue;
```

```jsx
let x = 3;
let y = 6;

x += y; // x = x + y
x -= y; // x = x - y
x *= y; // x = x * y
x /= y; // x = x / y
```

<table style="border-collapse: collapse; width: 100%; height: 266px;" border="1" data-ke-style="style15"><tbody><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;"><b>이름</b></td><td style="width: 33.3333%; height: 19px; text-align: center;"><b>복합 할당 연산자</b></td><td style="width: 33.3333%; height: 19px; text-align: center;"><b>뜻</b></td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">덧셈 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x += y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x + y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">뺄셈 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x -= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x - y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">곱셈 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x *= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x * y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">나눗셈 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x /= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x / y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">나머지 연산 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x %= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x % y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">지수 연산 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x **= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x ** y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">왼쪽 이동 연산 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x &lt;&lt;= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x &lt;&lt; y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">오른쪽 이동 연산 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x &gt;&gt;= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x &gt;&gt; y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">부호 없는 오른쪽 이동 연산 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x &gt;&gt;&gt;= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x &gt;&gt;&gt; y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">비트 AND 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x &amp;= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x &amp; y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">비트 XOR 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x ^= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x ^ y</td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px; text-align: center;">비트 OR 할당</td><td style="width: 33.3333%; height: 19px; text-align: center;">x |= y</td><td style="width: 33.3333%; height: 19px; text-align: center;">x = x | y</td></tr></tbody></table>

<br />


## 단항 연산자
연산자 뒤나 앞에 하나의 피연산자가 필요하다.
```jsx
// 피연산자   연산자
     x       ++        
```
<br />

### 증감 연산자
```jsx
let counter = 2;

const preIncrement = ++counter;
// counter = counter + 1;
// preIncrement = counter;

const postIncrement = counter++;
// postIncrement = counter;
// counter = counter + 1;

const preDecrement = --counter;
// counter = counter - 1;
// preDecrement = counter;

const postDecrement = counter--;
// postDecrement = counter;
// counter = counter - 1;
```

<br />

## 이항 연산자
하나는 좌변(피연산자1)에, 다른 하나(피연산자2)는 우변에 총 두 개의 피연산자가 필요하다.
```jsx
// 피연산자1   연산자   피연산자2
      1       +        2
```
<br />

### 산술 연산자
숫자 값(리터럴 또는 변수)을 피연산자로 갖고, 하나의 숫자 값을 반환한다.
- 기본적인 산술연산자는 덧셈(`+`), 뺄셈(`-`), 곱셈(`*`), 나눗셈(`/`)이다.
- 이 연산자들은 대부분의 다른 프로그래밍 언어들이 부동소수점 값을 연산하는 것 처럼 동작한다.
```jsx
console.log(1 + 2); // 더하기
console.log(2 - 1); // 빼기
console.log(3 * 2); // 곱하기
console.log(4 / 2); // 나누기
console.log(10 % 2); // 나머지
```
<br />

<table style="border-collapse: collapse; width: 100%; height: 190px;" border="1" data-ke-style="style15"><tbody><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;"><b>연산자</b></td><td style="width: 41.7054%; text-align: center; height: 19px;"><b>설명</b></td><td style="width: 38.9147%; text-align: center; height: 19px;"><b>예제</b></td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">더하기 연산자 ( + )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #333333;"><span style="color: #006dd7;">(이항)</span><span>&nbsp;</span></span>피연산자를 더한 값을 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">1 + 2 는 3을 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">뺴기 연산자 ( - )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #333333;"><span style="color: #006dd7;">(이항)</span><span>&nbsp;</span></span>피연산자를 뺀 값을 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">3 - 1 은 2를 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">곱하기 연산자 ( * )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #333333;"><span style="color: #006dd7;">(이항)</span><span>&nbsp;</span></span>피연산자를 곱한 값을 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">2 * 3 은 6을 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">나누기 연산자 ( / )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #333333;"><span style="color: #006dd7;">(이항)</span><span>&nbsp;</span></span>피연산자를 나눈 값을 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">8 / 2 는 4을 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">나머지 연산자 ( % )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #006dd7;">(이항)</span> 피연산자를 나눈 후 나머지를 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">12 % 5 는 2를 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">증가 연산자 ( ++ )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #006dd7;">(단항)</span> 피연산자에 1을 더한다. 만약 연산자를 피연산자<br>앞( ++a )에 사용하면, 피연산자에 1을 더한 값을 반환한다.<br>연산자를 피연산자 뒤( a++ )에 사용하면,<br>피연산자에 1을 더하기 전 값을 반환한다.</td><td style="width: 38.9147%; text-align: center; height: 19px;">a가 3이면 ++a는 a를 4로 만들고 4를 반환한다.<br>반면 a++는 3을 반환하고 a를 4로 만든다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">감소 연산자 ( -- )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #006dd7;">(단항)</span> 피연산자로&nbsp; 부터 1을 뺀다.&nbsp;</td><td style="width: 38.9147%; text-align: center; height: 19px;">a가 3이면 --a는 a를 2로 만들고 2를 반환한다.<br>반면 a--는 3을 반환하고 a를 2로 만든다.</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">단항 부정 연산자 ( - )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #006dd7;">(단항)</span><span style="color: #333333;"><span>&nbsp;</span>피연산자의 반대값(부호가 바뀐 값)을 반환한다.</span></td><td style="width: 38.9147%; text-align: center; height: 19px;">a가 3이면 -a 는 -3을 반환한다.&nbsp;</td></tr><tr style="height: 19px;"><td style="width: 19.3798%; text-align: center; height: 19px;">숫자화 연산자 ( + )</td><td style="width: 41.7054%; text-align: center; height: 19px;"><span style="color: #006dd7;">(단항)</span><span style="color: #333333;"><span>&nbsp;</span>피연산자가 숫자값이 아니라면 피연산자를 숫자로 변환하기를 시도한다.</span></td><td style="width: 38.9147%; text-align: center; height: 19px;">+"3"은 3을 반환한다.<br>+ture는 1을 반환한다.</td></tr></tbody></table>

<br />

### 문자 연산자
문자열 값으로 사용될 수 있는 비교 연산자에 덧붙여서, 연결 연산자 ( + ) 는 두 문자열 값을 연결하고, 두 문자열이 합쳐진 새로운 문자열을 반환한다.

```jsx
console.log('my' + ' name'); // my name
console.log('1' + 2); // 12
console.log(`string literals: 1 + 2 = ${1 + 2}`); // string literals: 1 + 2 = 3
```

<br />

### 비교 연산자
피연산자들을 비교하고, 비교에 따라 논리 값을 반환한다. 피연산자들은 숫자, 문자열, 논리형, 객체를 사용한다.

```jsx
console.log(10 < 6); // less than
console.log(10 <= 6); // less than or equal
console.log(10 > 6); // greater than
console.log(10 >=6); // greater than or equal
```

`==` : 타입을 바꿔서 값만 같으면 참을 반환 (지양)

`===` : 타입과 값이 모두 같아야 참을 반환 (지향)

```jsx
const stringFive = '5';
const numberFive = 5;

console.log(stringFive == numberFive); // true
console.log(stringFive != numberFive); // false

console.log(stringFive === numberFive); // false
console.log(stringFive !== numberFive); // true
```
단, 객체에서는 약간 다르다. 같은 값을 갖고 있더라도 각각 다른 레퍼런스를 가르키고 있기 때문!
```jsx
const lightix1 = { name: 'lightix'};
const lightix2 = { name: 'lightix'};
const lightix3 = lightix1;

console.log(lightix1 == lightix2); // false
console.log(lightix1 === lightix2); // false
console.log(lightix1 == lightix3); // true
```

문자열은 유니코드 값을 사용하여 표준 사전순서를 기반으로 비교한다. 만약 두 피연산자가 다른 형태일 경우, JavaScript는 대부분 비교를 위해 피연산자를 적절한 타입으로 변환한다. 이런 행동은 보통 숫자로 피연산자를 숫자로 비교하는 형태로 나타난다. 형태를 바꾸기의 유일한 예외는 엄격한 비교를 수행하는 `===` 과 `!==` 연산이 관련되는 경우다. 이런 연산자는 비교를 위해 피연산자의 형태를 적절히 바꾸려고 시도하지 않는다.
<table style="border-collapse: collapse; width: 100%; height: 171px;" border="1" data-ke-style="style15"><tbody><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;"><b>연산자</b></td><td style="width: 51.8218%; height: 19px; text-align: center;"><b>설명</b></td><td style="width: 26.7053%; height: 19px; text-align: center;"><b>true를 반환하는 예</b></td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">동등 ( == )</td><td style="width: 51.8218%; height: 19px; text-align: center;">피연산자들이 같으면 true를 반환한다.</td><td style="width: 26.7053%; height: 19px; text-align: center;">3 == a<br>"3" == a<br>3 == "3"</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">부등 ( != )</td><td style="width: 51.8218%; height: 19px; text-align: center;">피연산자들이 다르면 true를 반환한다.</td><td style="width: 26.7053%; height: 19px; text-align: center;">a != 4<br>b != "3"</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">일치 ( === )</td><td style="width: 51.8218%; height: 19px; text-align: center;">피연산자들이 같고, 피연산자들의 형태가 같을 경우 true를 반환한다.</td><td style="width: 26.7053%; height: 19px; text-align: center;">3 === a</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">불일치 ( !== )</td><td style="width: 51.8218%; height: 19px; text-align: center;">피연산자들이 다르거나 형태가 다른 경우 <span style="color: #333333;">true를 반환한다.</span></td><td style="width: 26.7053%; height: 19px; text-align: center;">a !== "3"<br>3 !== "3"</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">~ 보다 큰 ( &gt; )</td><td style="width: 51.8218%; height: 19px; text-align: center;">좌변의 피연산자보다 우변의 피연산자가 크면 <span style="color: #333333;">true를 반환한다.</span></td><td style="width: 26.7053%; height: 19px; text-align: center;">b &gt; a<br>"10" &gt; 3</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">~ 보다 크거나 같은 ( &gt;= )</td><td style="width: 51.8218%; height: 19px; text-align: center;">좌변의 피연산자보다 우변의 피연산자가 크거나 같으면 <span style="color: #333333;">true를 반환한다.</span></td><td style="width: 26.7053%; height: 19px; text-align: center;">b &gt;= a<br>a &gt;= 3</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">~ 보다 작은 ( &lt; )</td><td style="width: 51.8218%; height: 19px; text-align: center;">좌변의 피연산자보다 우변의 피연산자가 작으면 <span style="color: #333333;">true를 반환한다.</span></td><td style="width: 26.7053%; height: 19px; text-align: center;">a &lt; b<br>"5" &lt; 10</td></tr><tr style="height: 19px;"><td style="width: 21.4728%; height: 19px; text-align: center;">~ 보다 작거나 같은 ( &lt;= )</td><td style="width: 51.8218%; height: 19px; text-align: center;">좌변의 피연산자보다 우변의 피연산자가 작거나 같으면 <span style="color: #333333;">true를 반환한다.</span></td><td style="width: 26.7053%; height: 19px; text-align: center;">a &lt;= b<br>b &lt;= 5</td></tr></tbody></table>


<br />

## Logical operators (논리 연산자)
논리 연산자는 보통 불리언 값과 사용된다.

<br />

### or 연산자 (`||`)
하나라도 참인 경우 참으로 연산한다.

처음 나온 값이 참인 경우 뒤에는 연산하지 않기 때문에, 효율적인 코드 작성을 위해 빠르게 연산이 되는 값을 앞쪽에 두는 것이 바람직하다.
```jsx
const value1 = false;
const value2 = 4 < 2;

// || (or)
console.log(`or: ${value1 || value2 || check()}`); // or: true

function check() {
	for (let i = 0; i < 10; i++) {
		// wasting time
	console.log('blah blah');
	}
	return true;
}
```

### and 연산자 (`&&`)
모두 참인 경우 truthy(참 같은) 값으로 연산한다. 처음에 나온 값이 거짓일 경우 뒤는 연산을 하지 않기 때문에, 효율적인 코드 작성을 위해 빠르게 연산이 되는 값을 앞쪽에 두는 것이 바람직하다.

- `a && b` 라면 연산으로 귀결되는 값은 `a` 혹은 `b` 이다.
- `a`가 Truthy한 값이면, `b`가 결과 값이 되고, `a`가 Falsy한 값이면 `b`가 결과 값이 된다.
```jsx
const value1 = false;
const value2 = 4 < 2;

// && (and)
console.log(`and: ${value1 && value2 && check()}`); // and: false

function check() {
	for (let i = 0; i < 10; i++) {
		// wasting time
	console.log('blah blah');
	}
	return true;
}
```
null 을 체크할 때에도 많이 사용된다.
```jsx
// nullableObject && nullableObject.something
if (nullableObject != null) {
	nullableObject.something;
}
```

<br />

### 부정 연산자 (`!`)
참이면 거짓으로, 거짓이면 참으로 연산한다.
```jsx
const value = false;
console.log(!value); // true
```

<br />

불리언 값들과 사용될 때, 연산자는 불리언 값을 반환한다. 그러나, `&&` 과 `||` 연산자는 실제로 명시된 피연산자들 중 하나를 반환한다. 따라서 만약 이 연산자들이 불리언 값이 아닌 값들과 함께 쓰였을 때, 그들은 불리언 값이 아닌 값을 반환할지도 모른다.

```jsx
const a1 = true && true; // true
const a2 = true && false; // false
const a3 = false && ture; // false
const a4 = false && (3 == 4 ); // false
const a5 = "dog" && "cat"; // "cat"
const a6 = false && "cat"; // false
const a7 = "cat" && false; // false
```
```jsx
const a1 = true || true; // true
const a2 = false || true; // true
const a3 = true || false; // true
const a4 = false || (3 == 5); // false
const a5 = "dog" || "cat"; // "dog"
const a6 = false || "dog"; // "dog"
const a7 = "dog" || false; // "dog"
```
```jsx
const a1 = !true; // false
const a2 = !false; // true
const a3 = !"dog"; // false
```

### 📌 단락평가
논리연산자가 왼쪽에서 오른쪽으로 평가될 때, 논리 연산자는 다음의 규칙을 따라서 '단축 게산'으로 검사된다.

- `false && anything` 은 `false`로 단축 계산된다.
- `true || anything` 은 `true`로 단축 계산된다.
  
이 논리 규칙들은 항상 정확하다. 위에 anything 은 평가되지 않는다.


<br />

<table style="border-collapse: collapse; width: 100%; height: 95px;" border="1" data-ke-style="style15"><tbody><tr style="height: 19px;"><td style="width: 18.1007%; height: 19px; text-align: center;"><b>연산자</b></td><td style="width: 37.0543%; height: 19px; text-align: center;"><b>구문</b></td><td style="width: 44.8449%; height: 19px; text-align: center;"><b>설명</b></td></tr><tr style="height: 38px;"><td style="width: 18.1007%; height: 38px; text-align: center;">논리 AND ( &amp;&amp; )</td><td style="width: 37.0543%; height: 38px; text-align: center;">a &amp;&amp; b</td><td style="width: 44.8449%; height: 38px; text-align: center;">a를 true로 변환할 수 있는 경우 b를 반환하고,<br>그렇지 않으면 a를 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 18.1007%; height: 19px; text-align: center;">논리 OR ( || )</td><td style="width: 37.0543%; height: 19px; text-align: center;">a || b</td><td style="width: 44.8449%; height: 19px; text-align: center;">a를 true로 변환할 수 있으면 a를 반환하고,<br>그렇지 않으면 b를 반환한다.</td></tr><tr style="height: 19px;"><td style="width: 18.1007%; height: 19px; text-align: center;">논리 NOT ( ! )</td><td style="width: 37.0543%; height: 19px; text-align: center;">!a</td><td style="width: 44.8449%; height: 19px; text-align: center;">단일 피연산자를 true로 변환할 수 있으면 false를 반환하고,<br>그렇지 않으면 true를 반환한다.</td></tr></tbody></table>

<br />

## 조건(삼항) 연산자
조건 연산자는 자바스크립트에서 3개의 항을 사용하는 유일한 연산자다. 조건 연산자는 조건에 따라 2개의 값 중 하나를 가질 수 있다.
```jsx
조건 ? 참일 때 값 : 거짓일 때 값
```

<br />

## 쉼표 연산자
쉼표 연산자 ( , )는 두 피연산자를 평가하고, 마지막 피연산자의 값을 반환한다. 이 연산자는 주로 for 반복문 안에서 각각의 시간에 복수의 변수들을 갱신하기 위해 사용한다.

예를 들어, a는 각 변에 10개의 원소가 있는 2차원 배열일 때, 다음의 코드는 두 변수를 한번에 증가시키기 위해 쉼표 연산자를 사용했다. 이 코드는 배열의 대각선에 위치한 원소를 출력한다.
```jsx
const x = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
const a = [x, x, x, x, x];
for (let i = 0, j = 9; i <= j; i++, j--) { 
  console.log(`a[${i}][${j}] = ${a[i][j]}`); 
}
```

<br />

## 기타 단항 연산자

<br />

### delete 연산자
delete 연산자는 객체, 객체의 속성, 배열의 특정한 위치에 있는 객체를 삭제한다.
```jsx
delete obj;
delete obj.property;
delete obj[index];
delete property; // 이 경우, with 구문이 있어야 동작한다.
```
const 구문을 사용하지 않고 암묵적으로 선언된 변수를 삭제할 때 사용할 수 있다. 만약 delete 연산자의 동작이 성공했다면, delete 연산자는 속성이나 원소를 undefined로 설정한다. delete 연산자는 연산이 수행 가능할 때 true값을 반환한다. 수행이 불가능할 경우 false 값을 반환한다.
```jsx
x = 20;
const y = 30;
object = new Number();
object.name = 'lightix'; // name 속성을 만듦

delete.x; // 암묵적으로 선언된 경우 true
delete.y; // const로 선언된 경우 false
delete Math.pi; // 미리 정의된 속성의 경우 false
delete object.name; // 사용자가 정의한 속성의 경우 true
delete object; // 암묵적으로 선언된 경우 true
```

#### delete 연산자로 배열의 원소 삭제
배열의 원소를 삭제할 때, 배열의 길이에 영향을 주지 못한다.

예를 들어, `a[3], a[4]`를 삭제했다면, `a[3], a[4]`는 `undefined`(정의되지 않음) 상태가 된다. `delete` 연산자가 배열의 한 원소를 삭제하였을 때, 그 원소는 배열에 존재하지 않는다.
```jsx
const cafe = ["starbucks", "ediya", "coffeebean", "twosomeplace", "hollys"];
delete cafe[3];
console.log(cafe[3]); //undefined
```
 위 예제에서, `cafe[3]`은 `delete` 연산자에 의해 제거됐지만, `cafe[3]`은 아직 다룰 수 있고 `undefined`를 리턴한다.

만약 배열의 원소가 존재하지만 `undefined` 값을 갖고 싶으면, `delete` 연산자 대신 `undefined` 키워드를 사용하자.
```jsx
const cafe = ["starbucks", "ediya", "coffeebean", "twosomeplace", "hollys"];
cafe[3] = undefined;
console.log(cafe[3]); // undefined
```

### typeof 연산자

typeof 연산자는 피연산자 앞에 위치한다.
```jsx
typeof 피연산자;
typeof(피연산자);
```
피연산자의 타입을 나타내는 문자열을 반환한다.
```jsx
console.log(typeof 42); // "number"
console.log(typeof 'lightix'); // "string"
console.log(typeof true); // "boolean"
console.log(typeof undeclaredVariable); // "undefined"
```
undefined, boolean, number, string, symbol, function, object 를 리턴한다.
```jsx
// Numbers
typeof 37 === 'number';
typeof 3.14 === 'number';
typeof Math.LN2 === 'number';
typeof Infinity === 'number';
typeof NaN === 'number'; // Despite being "Not-A-Number"
typeof Number(1) === 'number'; // 사용 금지
typeof 42n === 'bigint';


// Strings
typeof "" === 'string';
typeof "bla" === 'string';
typeof (typeof 1) === 'string'; // typeof always returns a string
typeof String("abc") === 'string'; // 사용 금지


// Booleans
typeof true === 'boolean';
typeof false === 'boolean';
typeof Boolean(true) === 'boolean'; // 사용 금지


// Symbols
typeof Symbol() === 'symbol'
typeof Symbol('foo') === 'symbol'
typeof Symbol.iterator === 'symbol'


// Undefined
typeof undefined === 'undefined';
typeof declaredButUndefinedVariable === 'undefined';
typeof undeclaredVariable === 'undefined'; 


// Objects
typeof {a:1} === 'object';

// use Array.isArray or Object.prototype.toString.call
// to differentiate regular objects from arrays
typeof [1, 2, 4] === 'object';

typeof new Date() === 'object';


// The following is confusing. Don't use!
typeof new Boolean(true) === 'object'; 
typeof new Number(1) === 'object'; 
typeof new String("abc") === 'object';


// Functions
typeof function(){} === 'function';
typeof class C {} === 'function';
typeof Math.sin === 'function';
```

객체의 속성이 갖고있는 타입의 값을 반환한다.
```jsx
typeof document.lastModified; // returns "string"
typeof window.length;         // returns "number"
typeof Math.LN2;              // returns "number"
```

메소드와 함수를 함수로 반환한다.
```jsx
typeof blur;        // returns "function"
typeof eval;        // returns "function"
typeof parseInt;    // returns "function"
typeof shape.split; // returns "function"
```

미리 정의된 객체에 대해 다음과 같은 결과를 반환한다.
```jsx
typeof Date;     // returns "function"
typeof Function; // returns "function"
typeof Math;     // returns "object"
typeof Option;   // returns "function"
typeof String;   // returns "function"
```

<br />

## 관계 연산자
관계 연산자들을 비교하고, 비교의 참 여부에 기반하여 불리언 값을 반환한다.

<br />

### in 연산자
객체의 특정한 속성이 있는 경우 true를 반환한다.
```jsx
// propNameOrNumber 는 속성의 이름을 나타내는 문자열 또는 배열의 인덱스를 나타내는 숫자이고, objectName은 객체의 이름이다.
propNameOrNumber in objectName
```

```jsx
const cafe = ["starbucks", "ediya", "coffeebean", "twosomeplace", "hollys"];
0 in cafe;         // true
3 in cafe;         // true
10 in cafe;        // false
"ediya" in cafe;   // false (인덱스 번호를 지정해야한다)
"length" in cafe;  // true (배열의 기본속성)

// 내장객체
"PI" in Math;      // true

// 생성된 객체
const lightix = { name: "lightix", sex: "Male", birth: "1993"};
"name" in lightix; // true
"sex" in lightix;  // true
```

<br />

### instanceof 연산자
명시된 객체가 명시된 객체형이 맞는 경우 true를 반환한다.

```jsx
// objectName은 objectType과 비교할 객체의 이름이고, objectType은 Date 또는 Array와 같은 객체형이다.
objectName instanceof objectType
```
instanceof 연산자는 런타임에 객체의 형태를 확인할 필요가 있을 때 사용한다.
예를 들어, 예외가 발생했을 때, 예외의 형태에 따라 예외를 처리하는 코드로 나뉘게 할 수 있다.

```jsx
// instanceof 연산자를 theDay 객체가 Date 형의 객체인지 알아내는 코드
const theDay = new Date(1993, 12, 24);
console.log(theDay instanceof Date);   // true
```

<br />

## 연산자 우선순위
구문을 수행할 때 수행될 순서를 결정한다. 괄호를 통해 우선 순위를 재정의할 수 있다.

<table style="border-collapse: collapse; width: 100%; height: 323px;" border="1" data-ke-style="style15"><tbody><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><b>연산자 종류</b></td><td style="width: 76.1628%; height: 19px; text-align: center;"><b>연산자 형태</b></td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">맴버 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;"><span style="color: #333333;">.&nbsp; &nbsp;[]</span></td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">객체 호출 / 생성 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;"><span style="color: #333333;">()&nbsp; &nbsp;new</span></td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">부정 / 증가 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;"><span style="color: #333333;">!&nbsp; &nbsp;~&nbsp; &nbsp;-&nbsp; &nbsp;+&nbsp; &nbsp;++&nbsp; &nbsp;--&nbsp; &nbsp;typeof&nbsp; &nbsp;void&nbsp; &nbsp;delete</span></td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">곱셈 / 나눗셈 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;">*&nbsp; &nbsp;/&nbsp; &nbsp;%</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">덧셈 / 뺄셈 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;">+&nbsp; &nbsp;-</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">비트단위 시프트 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;">&lt;&lt;&nbsp; &nbsp;&gt;&gt;&nbsp; &nbsp;&gt;&gt;&gt;</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;"><span style="color: #333333;">관계 연산자</span></td><td style="width: 76.1628%; height: 19px; text-align: center;">&lt;&nbsp; &nbsp;&lt;=&nbsp; &nbsp;&gt;&nbsp; &nbsp;&gt;=&nbsp; &nbsp;in&nbsp; &nbsp;instanceof</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; height: 19px; text-align: center;">같음 비교 연산자</td><td style="width: 76.1628%; height: 19px; text-align: center;">==&nbsp; &nbsp;!=&nbsp; &nbsp;===&nbsp; &nbsp;!==</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">비트 단위 논리곱 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">&amp;</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">비트단위 배타적 논리합 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">^</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">비트단위 논리합 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">|</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">논리 곱 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">&amp;&amp;</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">논리 합 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">||</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">조건 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">? :</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">할당 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">=&nbsp; &nbsp;+=&nbsp; &nbsp;-=&nbsp; &nbsp;*=&nbsp; &nbsp;/=&nbsp; &nbsp;%=&nbsp; &nbsp;&lt;&lt;=&nbsp; &nbsp;&gt;&gt;=&nbsp; &nbsp;&gt;&gt;&gt;=&nbsp; &nbsp;&amp;=&nbsp; &nbsp;^=&nbsp; &nbsp;|=</td></tr><tr style="height: 19px;"><td style="width: 23.8372%; text-align: center; height: 19px;">콤마 연산자</td><td style="width: 76.1628%; text-align: center; height: 19px;">,</td></tr></tbody></table>

###### 우선순위 높은 순서부터 낮은 순서로 설명하고 있다.

<br />

출처 - [Mozilla 표현식과 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators)