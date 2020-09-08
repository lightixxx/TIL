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
배열의 요소를 모두 출력한다.
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

for(let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // 'apple', 'banana', 'kiwi', 'strawberry'
}
```


<br />

### 역 for 반복문
배열의 요소를 모두 반대로 출력한다.
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

for(let i = fruits.length - 1; i >= 0; i--) {
  console.log(fruits[i]); // 'strawberry', 'kiwi', 'banana', 'apple'
}
```

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
- `for(요소 in 배열) {실행할 코드}`

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

### forEach( )
배열 안에 각각의 element에 같은 코드를 수행하게 한다.
- forEach()의 인자값은 callback function이다.
- forEach()는 return, break, continue가 불가능하다.
```jsx
const fruits = ['apple', 'banana', 'kiwi', 'strawberry'];

fruits.forEach(fruit => console.log(fruit));
```

<br />

## Addition, deletion, sorting
배열은 많은 데이터를 효율적으로 관리, 전달하기 위한 목적으로 고안된 데이터 타입이다. 따라서 데이터의 추가, 수정, 삭제, 정렬과 같은 일을 편리하게 할 수 있는 기능을 갖고 있다.

<br />

---
## Addition
<br />

### push( )
인자로 전달된 값을 배열의 끝에 추가
```jsx
const arr = [1, 2, 3];
arr.push(4);

console.log(arr); // [1, 2, 3, 4]
```

<br />

### concat( )
인자로 전달된 복수의 값을 추가
```jsx
const arr = ['a', 'b', 'c', 'd'];
arr.concat(['e', 'f']);

console.log(arr); // ['a', 'b', 'c', 'd', 'e', 'f']
```

<br />

### unshift( )
인자로 전달된 값을 배열의 앞에 추가
```jsx
const arr = [1, 2, 3];
arr.unshift(0);

console.log(arr); // [0, 1, 2, 3]
```

<br />

### splice( )
첫번째 인자에 해당하는 원소부터 두번째 인자에 해당하는 원소의 숫자만큼의 값을 제거한 뒤 세번째 인자부터 전달된 인자들을 첫번째 인자의 원소 뒤에 추가
- `splice(index, 제거할 요소의 개수, 배열에 추가할 요소)`
- 제거할 개수를 작성하지 않으면 첫번째 인자 값부터 모두 제거된다.
```jsx
const arr = [1, 2, 3, 4, 5];
arr.splice(2, 0, 2.5);

console.log(arr); // [1, 2, 2.5, 3, 4, 5]
```
<br />

---
## Deletion
<br />

### shift( )
배열의 첫번째 원소를 제거
```jsx
const arr = [1, 2, 3, 4];
arr.shift();

console.log(arr); // [2, 3, 4]
```

<br />

### pop( )
배열의 끝 원소를 제거
- 제거된 원소를 리턴
```jsx
const arr = [1, 2, 3, 4];
arr.pop();

console.log(arr); // [1, 2, 3]
```
<br />

#### 📌 shift / unshift는 push / pop보다 느리다 !
##### push / pop은 맨 뒤에 추가,제거만 하기 때문에 다른 원소의 인덱스에 영향이 없다. 하지만 shift / unshift는 앞에 추가,제거 되기 때문에 모든 원소의 인덱스가 바뀌기 때문에 처리 속도가 느리다.

<br />

---
## Sorting

<br />

### sort( )
배열의 내용을 순서대로 정렬
```jsx
const arr = [3, 5, 2, 1, 4];
arr.sort();

console.log(arr); // [1, 2, 3, 4, 5]
```

<br />

### reverse( )
배열의 내용을 역순으로 정렬
- sort와 함께 사용하면 내림차순으로 정렬할 수 있다.
```jsx
const arr = [3, 5, 2, 1, 4];
arr.reverse();

console.log(arr); // [4, 1, 2, 5, 3]
```

<br />

---

## Searching
배열의 요소를 찾아서 다양한 처리를 할 수 있다

<br />

### indexOf( )
인자에 넣은 값이 몇 번째 인덱스에 있는지 찾아서 해당 인덱스를 리턴
- 중복된 값이 있다면 앞에 있는 인덱스를 리턴
- 해당 값이 없으면 -1을 리턴
```jsx
const arr = ['kim', 'lee', 'park', 'choi'];
const leeIndex = arr.indexOf('lee');
const bangIndex = arr.indexOf('bang');

console.log(leeIndex); // 1
console.log(bangIndex); // -1
```

<br />

### lastIndexOf( )
인자에 넣은 값이 몇 번째 인덱스에 있는지 찾아서 마지막 인덱스를 리턴
```jsx
const arr = [24, 26, 27, 28, 30, 26];
const lastIndexArr = arr.lastIndexOf(26);

console.log(lastIndexArr); // 5
```

<br />

## API (Application Programming Interface)
그 밖에 유용한 api

---
<br />

### join( )
배열에 있는 모든 원소를 더해서 문자열로 리턴
- 인자 값으로 원소 사이에 string 값을 추가할 수도 있다.
```jsx
const arr = [1, 2, 3, 4, 5];
console.log(arr.join()); // 1,2,3,4,5
console.log(arr.join(' & ')); // 1 & 2 & 3 & 4 5
```

<br />

### split( )
인자값으로 구분자를 넣어서 string을 배열로 만듦
- 리턴받을 배열의 사이즈도 정할 수 있다.
```jsx
const fruits = 'apple, banana, kiwi, strawberry';
const result = fruits.split();
console.log(result); // ['apple, banana, kiwi, strawberry']

const result2 = fruits.split(', ');
console.log(result2); // ['apple', 'banana', 'kiwi', 'strawberry']

const result3 = fruits.split(', ', 2);
console.log(result3); // ['apple', 'banana']
```

<br />

### slice ()
배열의 일부분을 선택해서 새로운 배열을 만듦
- `.slice(start, end)`
```jsx
const arr = [1, 2, 3, 4, 5];
const result = arr.slice(2, 5);

console.log(result); // [3, 4, 5]
```