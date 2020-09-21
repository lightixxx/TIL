# Date 객체
날짜와 시간을 위한 메서드를 제공하는 빌트인 객체이면서 생성자 함수이다. 날짜와 시간은 자바스크립트 코드가 동작한 시스템의 시계에 의해 결정된다. 시스템 시계의 설정에 따라 서로 다른 값을 가질 수 있다.

<br />

## Date Constructor
Date 생성자 함수는 날짜와 시간을 가지는 인스턴스를 생성한다. 생성된 인스턴스는 현재 날짜와 시간을 나타내는 값을 갖는다.

<br />

### new Date()
인수를 전달하지 않으면 현재 날짜와 시간을 갖는 인스턴스를 리턴한다.
```jsx
const date = new Date();
console.log(date); // Sat Sep 19 2020 20:54:36 GMT+0900 (대한민국 표준시)
```

### new Date(dateString)
인수로 문자열을 전달해서 지정된 날짜와 시간을 갖는 인스턴스를 반환한다. 문자열은 Date.parse 메소드로 해석이 가능한 형식이어야 하기 때문에 한글은 전달할 수 없다.
- 문자열 외에도 인수로 숫자를 연, 월-1, 일, 시, 분, 초, 밀리 초 순서로 입력할 수도 있다.
- 0월부터 시작하기 때문에 월 - 1을 입력해야 원하는 값을 갖는다.
```jsx
let date = new Date('December 24, 1993');
console.log(date); // Fri Dec 24 1993 00:00:00 GMT+0900 (대한민국 표준시)
date = new Date('1993/12/24/12:24:12');
console.log(date); // Fri Dec 24 1993 12:24:12 GMT+0900 (대한민국 표준시)
```

### new 연산자없이 Date 호출
Date 생성자 함수를 new 연산자 없이 호출하면 인스턴스를 리턴하지 않고 결과값을 문자열로 리턴한다.
```jsx
let date = Date();
console.log(typeof date, date); // string Sat Sep 19 2020 21:13:15 GMT+0900 (대한민국 표준시)
```

## Date Method
Date 객체의 메서드는 크게 세 가지로 분류할 수 있다.
1. getOO()
2. setOO()
3. toOOString()

너무 많으니까 중요해 보이는 것만 알고 나머지는 필요할 때마다 찾아서 쓰자..

<br />

### Date.getDate()
날짜(일)를 나타내는 정수를 리턴한다.

```jsx
const today = new Date();
const date = today.getDate();

console.log(today); // Sat Sep 19 2020 21:22:08 GMT+0900 (대한민국 표준시)
console.log(date); // 19
```

### Date.setDate()
날짜(일)를 나타내는 정수를 설정한다.

```jsx
const today = new Date();

// 날짜를 12일로 지정
today.setDate(12);

const date = today.getDate();
console.log(today);
console.log(date);
```

> 연도와 관련된 메서드 중 이름이 비슷한 `getYear()` 메서드와 `getFullYear()` 메서드가 있다. `getYear()` 메서드는 웹 브라우저에 따라 조금씩 다른 결과를 출력하기 때문에 `getFullYear()` 메서드를 사용하는 것이 좋다.

`Date` 객체는 getter와 setter 이외에 `toOOstring()` 형태의 메서드도 있다.

### Date.toDateString
읽을 수 있는 형식의 문자열로 날짜를 리턴한다.
```jsx
const date = new Date('1993/12/24/11:11');
console.log(date); // Fri Dec 24 1993 11:11:00
```
<br />

## Date Example
<br />

### 일주일 후의 시간 구하기
```jsx
const date = new Date(); // Sat Sep 19 2020 21:29:05 GMT+0900

date.setDate(date.getDate() + 7);
console.log(date); // Sat Sep 26 2020 21:29:05 GMT+0900
```

### D-day 구하기
날짜 간격을 구할 땐 `getTime()`함수를 사용한다. `getTime()` 함수는 1970년 1월 1일 자정부터 지난 밀리초를 구한다. 이를 사용해서 두 시간 사이의 초 간격을 구하고 다시 날짜로 바꾼다.
```jsx
// 변수를 선언한다.
const now = new Date();
const cristmas = new Date(`December 25, 2020`);

// 날짜 간격을 구한다.
let dDay = now.getTime() - cristmas.getTime();
dDay = Math.floor(dDay / (1000 * 60 * 60 * 24));

// 출력한다.
console.log(`D-day: ${dDay}일`);
```