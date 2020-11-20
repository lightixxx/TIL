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
배열의 요소를 제거하는 방법.
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

#### 📌 shift / unshift는 push / pop보다 느리다.
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
배열의 요소를 찾아서 다양한 처리를 할 수 있다.

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
<br />

### 유용한 배열 함수 10가지 (with.드림코딩 엘리)
<br />

#### 1. 주어진 배열을 string으로 변환하기 
  - `join(seperator? : string);`
```jsx
const fruits = ['apple', 'banana', 'orange'];
const result = fruits.join();
console.log(result); // apple, banana, orange
```

<br />

#### 2. 주어진 string을 배열로 변환하기 
  - `split(seperator: string, limit?: number): string[];`
```jsx
const fruits = 'apple, banana, orange';
const result = fruits.split(', ');
console.log(result); // ['apple', 'banana', 'orange']
```
<br />

#### 3. 주어진 배열의 순서를 거꾸로 만들기
  - `reverse(seperator? : string);`
  - 배열 자체 값도 변하고, 변화된 배열을 `return`한다.
```jsx
const array = [1, 2, 3, 4, 5];
const result = array.reverse();
console.log(result); // apple, banana, orange
```

<br />

#### 4. 주어진 배열에서 요소를 제거해서 새로운 배열 만들기
  - `slice(start? : number, end? : number);`
  - `splice()`는 배열 자체를 수정하지만, `slice()`는 수정하지 않는다.
```jsx
const array = [1, 2, 3, 4, 5];
const result = array.slice(2, 5);
console.log(result); // [3, 4, 5]
console.log(array); // [1, 2, 3, 4, 5]
```

<br />
<br />

```jsx
class Student {
  constructor(name, age, enrolled, score) {
    this.name = name;
    this.age = age;
    this.enrolled = enrolled;
    this.score = score;
  }
}

const students = [
  new Student('A', 29, true, 45),
  new Student('B', 28, false, 80),
  new Student('C', 30, true, 90),
  new Student('D', 40, false, 66),
  new Student('E', 18, true, 88),
];
```

#### 5. 학생의 점수가 90점인 학생 찾기
  - `find(predicate: (), thisArg?);`
  - predicate에는 불리언 값으로 정의될 수 있는 callback 함수를 받는다.
  - predicate에 전달된 함수가 `true`일 경우 찾아진 요소를 `return`한다.
```jsx
const result = students.find(student => student.score === 90);
```

<br />

#### 6. 수업에 등록한 학생만 골라내기
  - `filter(callback);`
  - callback 함수가 `true`인 것들만 모아서 배열을 리턴한다.
```jsx
const result = students.filter(student => student.enrolled);
```

<br />

#### 7. 학생들의 점수만 뽑아서 배열로 만들기
  - `map(callback);`
  - 배열 안에 들어있는 모든 요소를 전달한 callback 함수를 거쳐서 다른 것으로 변환해 주는 것을 말한다.
```jsx
const result = students.map(student => student.score);
```
<br />

#### 8. 점수가 50점 이하인 학생이 있는지 확인하기
  - `some(callback);`
  - 배열의 요소 중, callback 함수가 `true`가 되는 요소가 한 개라도 있으면 `true`를 `return`하는 API이다.
  - 비슷하게 `every()`는 모든 요소가 `true`가 되어야 `true`를 `return`한다.
```jsx
const result = students.some(student => student.score < 50);
```
<br />

#### 9. 학생들의 평균 점수 구하기
  - `reduce(callback(prev, curr), initialValue?);`
  - callback 함수나, initialValue를 전달하고, 배열의 요소마다 호출이 된다.
  - callback 함수에서 누적된 결과값을 `return`한다.
```jsx
const result = students.reduce((prev, curr) => prev + curr.score / students.length, 0);
```
<br />

#### 10. 모든 점수를 string으로 변환하기
  - `map()`은 새로 만들어진 배열 자체를 `return`하기 때문에, API들을 섞어서 활용할 수 있다.
```jsx
const result = students.map(student => student.score).join();
```

<br />

#### bonus. 모든 점수를 string으로 변환하고 점수순대로 정렬하기
  - `sort()`
  - callback 함수에는 a, b 즉, 이전 값과 현재 값이 전달이 되는데, 음수를 `return`하게 되면, 처음 오는 값이 다음에 오는 값보다 작다고 간주되어서 정렬이 된다.
```jsx
const result = students.map(student => student.score)
.sort((a, b) => a - b)
.join();
```

<br />

##### 출처
- [드림코딩엘리](https://youtu.be/3CUjtKJ7PJg)