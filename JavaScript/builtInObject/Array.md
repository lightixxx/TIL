# Array 객체
여러 가지 자료를 쉽게 관리할 수 있게 도와주는 객체이다.

## Property

<br />

### Array.length
`length` 프로퍼티는 요소의 개수(배열의 길이)를 나타낸다.

<br />

## Method
배열은 많은 데이터를 효율적으로 관리, 전달하기 위한 목적으로 고안된 데이터 타입이다. 따라서 데이터의 추가, 수정, 삭제, 정렬과 같은 일을 편리하게 할 수 있는 기능을 갖고 있다.

<br />

## Addition

<br />

### push( )
인자로 전달된 값을 배열의 끝에 추가한다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [1, 2, 3];
arr.push(4);

console.log(arr); // [1, 2, 3, 4]
```

<br />

### concat( )
인자로 전달된 복수의 값을 추가한다.

```jsx
const arr = ['a', 'b', 'c', 'd'];
arr.concat(['e', 'f']);

console.log(arr); // ['a', 'b', 'c', 'd', 'e', 'f']
```

<br />

### unshift( )
인자로 전달된 값을 배열의 앞에 추가한다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [1, 2, 3];
arr.unshift(0);

console.log(arr); // [0, 1, 2, 3]
```

<br />

### splice( )
첫번째 인자에 해당하는 원소부터 두번째 인자에 해당하는 원소의 숫자만큼의 값을 제거한 뒤 세번째 인자부터 전달된 인자들을 첫번째 인자의 원소 뒤에 추가한다.
- `splice(index, 제거할 요소의 개수, 배열에 추가할 요소)`
- 제거할 개수를 작성하지 않으면 첫번째 인자 값부터 모두 제거된다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [1, 2, 3, 4, 5];
arr.splice(2, 0, 2.5);

console.log(arr); // [1, 2, 2.5, 3, 4, 5]
```
<br />

## Deletion

<br />

### shift( )
배열의 첫번째 원소를 제거한다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [1, 2, 3, 4];
arr.shift();

console.log(arr); // [2, 3, 4]
```

<br />

### pop( )
배열의 끝 원소를 제거한다.
- 제거된 원소를 리턴한다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [1, 2, 3, 4];
arr.pop();

console.log(arr); // [1, 2, 3]
```
<br />

#### 📌 shift / unshift는 push / pop보다 느리다 !
##### push / pop은 맨 뒤에 추가,제거만 하기 때문에 다른 원소의 인덱스에 영향이 없다. 하지만 shift / unshift는 앞에 추가,제거 되기 때문에 모든 원소의 인덱스가 바뀌기 때문에 처리 속도가 느리다.

<br />

## Sorting

<br />

### sort( )
배열의 내용을 순서대로 정렬한다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [3, 5, 2, 1, 4];
arr.sort();

console.log(arr); // [1, 2, 3, 4, 5]
```

<br />

### reverse( )
배열의 내용을 역순으로 정렬
- sort와 함께 사용하면 내림차순으로 정렬할 수 있다.
- 자기 자신을 변화시키는 메서드이다.
```jsx
const arr = [3, 5, 2, 1, 4];
arr.reverse();

console.log(arr); // [4, 1, 2, 5, 3]
```

<br />


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

### find( )
주어진 판별 함수를 만족하는 첫 번째 요소의 값을 반환한다. 요소가 없다면 `undefined`를 반환한다.
```jsx
const arr = [1, 2, 5, 8, 13, 22, 55];
const arr2 = arr.find(elem => elem > 11 );

console.log(arr2); // 13
```

<br />

## API (Application Programming Interface)
그 밖에 유용한 API

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
배열의 일부분을 선택해서 새로운 배열을 만든다.
- `.slice(start, end)`
```jsx
const arr = [1, 2, 3, 4, 5];
const result = arr.slice(2, 5);

console.log(result); // [3, 4, 5]
```

<br />

### map()
배열 내의 모든 요소에 대해 주어진 콜백 함수를 호출한 결과를 가진 새로운 배열을 만든다. 반복문을 돌며 배열 안의 요소들을 매핑해주고 기존의 배열은 수정하지 않고 새로운 배열을 만든다. 단, 배열 안에 객체가 있는 경우 객체는 공유된다.

- `arr.map((요소, 인덱스, 배열) => {return 요소});`
   
```jsx
const arr = [1, 2, 3, 4, 5];

let newArr = arr.map((v) => {
  return v + 1;
})

console.log(arr); // [1, 2, 3, 4, 5]
console.log(newArr); // [2, 3, 4, 5, 6]
```

콜백함수로 다양하게 리턴할 수 있기 때문에 자유도가 높다.
```jsx
const arr = [1, 2, 3, 4, 5];

let result = arr.map((v) => {
  if(v % 2 === 0) {
    return '짝';
  }
  return '홀';
})

console.log(arr); // [1, 2, 3, 4, 5]
console.log(result); // ['홀', '짝', '홀', '짝', '홀']
```

<br />

### forEach()
for문 대신 사용할 수 있다. 배열을 순회해서 각 요소에 대하여 인자로 주어진 콜백함수를 실행한다. `undefined`를 리턴한다. 콜백 함수의 매개변수를 통해 배열의 요소 값, 인덱스, 메서드를 호출한 배열(`this`)를 전달받을 수 있다.
- `forEach(function(item, index, self) { })`
```jsx
// for문 사용 시
const numbers = [1, 2, 3, 4, 5];
let pows = [];

for(let i = 0; i < numbers.length; i++) {
  pows.push(numbers[i] ** 2);
}

console.log(pows); // [1, 4, 9, 16, 25]
```
```jsx
// forEach() 사용시
const numbers = [1, 2, 3, 4, 5];
let pows = [];

numbers.forEach(item => pows.push(item ** 2));

console.log(pows); // [1, 4, 9, 16, 25]
```

<br />

### reduce()

- `arr.reduce((누적 값, 현재 값, 인덱스, 요소) => {return 결과}, 초기 값)`

```jsx
const numbers = [1, 2, 3, 4, 5];

const result = numbers.reduce((acc, cur, i) => {
  console.log(acc, cur, i);
  return acc + cur;
}, 0);

result; // 15

// acc, cur, i
// 0 1 0
// 1 2 1
// 3 3 2
// 6 4 3
// 10 5 4
```