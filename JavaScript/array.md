# Array (배열)
연관된 데이터를 묶어서 한 곳에 보관하는 개념이다. 여러개의 변수를 한꺼번에 선언해 다룰 수 있는 자료형이다.


<br />

## 📌 여기서 꼭 알아야 할 용어
- Element (원소) : 배열 안에 입력된 값
- Index (색인) : 배열에 담겨있는 값을 가져올 때 사용하는 숫자 (0부터 시작)

<br />

## 배열을 만드는 방법
```jsx
const array1 = [1, 2];
const array2 = new Array();
```

<br />

## Index position
```jsx
const fruits = ['🍎', '🍌'];
console.log(fruits); //["🍎", "🍌"]
console.log(fruits.length); // 2
console.log(fruits[1]); // 🍌
console.log(fruits[fruits.length - 1]; // 배열의 마지막에있는 아이템을 찾을 때
```
##### `배열.length` 속성으로 현재 배열에 요소가 몇 개 있는지 확인할 수 있다.

<br />

## Looping
배열은 반복문으로 리스트에 담긴 정보를 하나씩 꺼내서 처리할 수 있기 때문에 자주 사용된다.

<br />

### for 반복문
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

for(let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // 'apple', 'banana', 'kiwi', 'strawberry'
}
```
##### 배열의 요소를 모두 출력한다.

<br />

### 역 for 반복문
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

for(let i = fruits.length - 1; i >= 0; i--) {
  console.log(fruits[i]); // 'strawberry', 'kiwi', 'banana', 'apple'
}
```
##### 배열의 요소를 모두 반대로 출력한다.

<br />

### for in 반복문
객체의 속성을 순회하기 위한 구문

`for(인덱스 in 배열) {실행할 코드}`
```jsx
const arr = [1, 2, 3, 4];

for(let i in arr) {
  console.log(`${i}번째 요소는 ${arr[i]}입니다.`);
  // 0번째 요소는 1입니다.
  // ...
  // 3번째 요소는 4입니다.
}
```

<br />

### for of 반복문 (ES6)
반복 가능한 객체에서 객체의 요소를 순회하기 위한 구문

`for(요소 in 배열) {실행할 코드}`

```jsx
const arr = [1, 2, 3, 4];

for(let el of arr) {
  console.log(`요소는 ${el}입니다.`);
  // 요소는 1입니다.
  // ...
  // 요소는 4입니다.
}
```

#### 📌 for-in은 반복 변수에 '인덱스'가, for-of는 '요소'가 들어간다.

<br />

### forEach()
배열 안에 각각의 element에 같은 코드를 수행하게 한다.
- forEach()의 인자값은 callback function이다.
- forEach()는 return, break, continue가 불가능하다.
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

fruits.forEach(fruit => console.log(fruit));
```

<br />

## Addition, deletion, copy

<br />

### push
배열의 끝에 원소를 추가
```jsx
const arr = [1, 2, 3];
arr.push(4);
```

