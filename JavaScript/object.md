# Object (객체)
함수, 클래스로 틀을 만들어진 key와 value의 집합체이다. 배열은 아이템에 대한 식별자로 숫자를 사용하는 반면, 객체는 식별자로 문자를 사용할 수 있다.


<br />

## 📌 여기서 꼭 알아야 할 용어
- Property (속성) : 객체가 가진 값
- Method (메서드) : 객체가 가진 속성 중 함수인 것
- Key (키) : 접근할 수 있는 변수 혹은 프로퍼티
- Value (값) : key가 갖고있는 값

<br />

## 객체를 만드는 방법
```jsx
const obj1 = {}; // object literal
const obj2 = new Object(); // object constructor
const obj3 = Object.create();
```
1. `obj1` 은 가장 직관적이고 간단하게 객체를 만드는 방법으로 간편하게 key와 value를 정의할 수 있다.
2. `obj2` 는 객체 생성자 함수를 사용하는 것이다. Object 앞에 new 키워드를 붙여서 만들 수 있지만 첫번째 방법이 더 쉽고 직관적이다.
3. `obj3` 는 메소드를 이용하는 방법이다. 반드시 값을 메소드에 전달해야 하고, null 또는 객체 타입만 사용할 수 있다. 메소드에 전달된 값을 만들고 있는 객체의 프로토타입으로 설정된다.

<br />

객체를 선언할 때는 `{ }` 안에 원하는 값을 넣으면 된다.
```jsx
키 : 원하는 값,
key : value
```
📌 key 값에는 공백이 없어야 한다. 공백이 있어야 하는 상황이라면 따옴표로 감싼다.

<br />

객체없이 변수로만 코드를 작성한다면, 그룹으로 묶어서 관리가 어려워진다.

```jsx
// 객체가 없다면
const name = 'lightix';
const age = 28
print(name,age);
function print(name, age) {
  console.log(name);
  console.log(age);
}

// 객체를 사용하면
function print(person) {
  console.log(person.name);
  console.log(person.age);
};

const lightix = {
  name: 'lightix',
  age: 28
};

print(lightix);
```

<br />

### 함수에서 객체를 파라미터로 받기
함수를 만들고 객체를 파라미터로 받아서 사용
```jsx
const lightix = {
  name: 'kiwoong',
  
}
```




<br />

자바스크립트는 런타임 때 동적으로 타입이 결정되는 언어이기 때문에, 나중에 프로퍼티를 추가 및 삭제할 수 있다. 단, 유지보수 측면에서는 좋지 않은 습관이다.
```jsx
lightix.hasjob = false;
console.log(lightix.hasJob) // false

delete lightix.hasJob;
console.log(lightix.hasJob); // undefined
```
