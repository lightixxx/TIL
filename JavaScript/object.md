# Object (객체)

객체란, 현실세계에서 인지하는 물체에 대한 모델을 만들기 위해 변수와 함수를 그룹화한 것을 말한다. 자바스크립트의 객체는 키와 값으로 구성된 프로퍼티들의 집합이다. 프로퍼티의 값으로 자바스크립트에서 사용할 수 있는 모든 값을 사용할 수 있다.

- 배열은 아이템에 대한 식별자로 숫자를 사용하는 반면, 객체는 식별자로 문자를 사용할 수 있다.
- 객체는 함수 혹은 클래스로 틀을 만드는 것이다.
- 자바스크립트의 객체는 객체지향의 상속을 구현하기위해 "프로토타입"이라고 불리는 객체의 프로퍼티와 메소드를 상속받을 수 있다.


<br />

## 📌 여기서 꼭 알아야 할 용어
- Property (속성) : 객체가 가진 값
- Method (메서드) : 객체가 가진 속성 중 함수인 것
- Key (키) : 접근할 수 있는 변수 혹은 프로퍼티
- Value (값) : key가 갖고있는 값

<br />


## 객체가 필요한 이유
객체없이 변수로만 코드를 작성한다면, 그룹으로 묶어서 관리가 어려워진다. 예를 들어 정보에 다른 값을 추가하게 된다면 코드의 수정이 복잡해지기 때문에 객체를 사용한다.
```jsx
// 객체가 없다면
const name = 'lightix';
const age = 28
print(name, age);
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

## 객체를 만드는 방법
```jsx
const obj1 = {}; // literal notation
const obj2 = new Object(); // object constructor
const obj3 = Object.create();
```
1. `obj1` 은 가장 직관적이고 간단하게 객체를 만드는 방법으로 간편하게 key와 value를 정의할 수 있다.
2. `obj2` 는 객체 생성자 함수를 사용하는 것이다. Object 앞에 new 키워드를 붙여서 만들 수 있지만 첫번째 방법이 더 쉽고 직관적이다.
3. `obj3` 는 메소드를 이용하는 방법이다. 반드시 값을 메소드에 전달해야 하고, null 또는 객체 타입만 사용할 수 있다. 메소드에 전달된 값을 만들고 있는 객체의 프로토타입으로 설정된다.

<br />

객체를 선언할 때는 `{ }` 안에 원하는 값을 넣으면 된다.
```jsx
'키' : '원하는 값',
'key' : 'value'
```
📌 key 값에는 공백이 없어야 한다. 공백이 있어야 하는 상황이라면 따옴표로 감싼다.

📌 각 키와 값은 콜론 (:) 으로 구분하고, 각 속성과 메서드는 쉼표(,) 로 구분한다.

<br />

### Literal

가장 일반적인 자바스크립트의 객체 생성 방식이다. 중괄호`{ }` 를 이용해서 객체를 생성하는데, 1개 이상의 프로퍼티를 작성하면 해당 프로퍼티가 추가된 객체를 생성할 수 있다. `{ }` 안에 아무것도 작성하지 않으면 빈객체가 생성된다.
```jsx
const emptyObj = {};
console.log(typeof emptyObject); // object

const lightix = {
  name: 'kiwoong',
  sex: 'male',
  favoriteFood: 'ramen',
  eat: function() {
    console.log(`${this.favoriteFood}을(를) 먹는다.`);
  }
};
```

<br />

### Object constructor function
`new` 연산자와 Object 생성자 함수를 호출하여 빈 객체를 만들 수 있다. 빈 객체 생성 이후 프로퍼티 또는 메소드를 추가해서 객체를 완성하는 방법이다. 생성자 함수란 new 키워드와 함께 객체를 생성하고 초기화하는 함수를 말한다. 생성자 함수를 통해 생성된 객체를 인스턴스라고 한다.

객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당하면 해당 객체에 프로퍼티를 추가하고 값을 할당한다. 이미 존재하는 키에 새로운 값을 할당하면 프로퍼티 값은 할당한 값으로 덮어 씌워진다.

```jsx
const lightix = new Object();

// 프로퍼티 추가
lightix.name = 'kiwoong';
lightix.sex = 'male';
lightix.favoriteFood = 'ramen';
lightix.eat = function () {
  console.log(`${this.favoriteFood}을(를) 먹는다.`);
}
```
특별한 이유가 없다면 객체 리터럴을 이용하는 것이 간편하다.

<br />

### Constructor function
프로퍼티 값만 다른 여러 개의 객체를 생성할 때, 위 두 가지 방법은 같은 프로퍼티를 매번 작성하는 것은 매우 불편한 일이다. 생성자 함수를 사용하면 마치 객체를 생성하기 위한 템플릿처럼 사용해서 프로퍼티가 동일한 객체 여러 개를 간편하게 만들 수 있다.

```jsx
// 생성자 함수
function Person(name, sex, favoriteFood) {
  this.name = name;
  this.sex = sex;
  this.favoriteFood = favoriteFood;
  this.eat = function() {
    console.log(`${this.favoriteFood}을(를) 먹는다.`);
  }
}

// 인스턴스 생성
const lightix = new Person('kiwoong', 'male', 'ramen');
const lvvrvsh = new Person('seungsoo', 'male', 'pizza');
```
#### 간단한 사용법만 알아보고 자세한 생성자 함수는 이후에 추가될 [constructorFunction](https://github.com/lightixxx/TIL/blob/master/JavaScript/constructorFunction.md)에 정리

<br />

## 객체에 접근하는 방법
```jsx
const lightix = {
  name: 'kiwoong',
  age: 28,
  eat: function(food) {
    console.log(`${food}을(를) 먹는다.`);
  }
}

// 마침표 표기법
const lightixAge = lightix.age; // Property
const lightixEat = lightix.eat('라면'); // Method

// 대괄호 표기법
const lightixName = lightix['name'];

function printValue(obj, key) {
  console.log(obj.key); // undefined
  console.log(obj[key]); // lightix
}
printValue(lightix, 'name');
```
1. Dot Notation(마침표 표기법)은 객체의 속성이나 메서드에 접근하기 위해 객체의 이름과 마침표를 작성한 다음 접근하고자 하는 속성이나 메서드의 이름을 작성하는 방법이다.
2. Square Bracket Notation(대괄호 표기법)은 객체의 이름 다음에 대괄호 안에 속성의 이름(문자열)을 입력하는 방법이다.
   * 프로퍼티 이름이 유효한 자바스크립트 이름이 아닌 경우에 사용한다.
   * 프로퍼티 이름이 예약어인 경우에 사용한다.
   * 속성의 이름이 숫자인 경우에 사용한다.(기술적으로는 가능하지만 일반적으로는 기피하는 방법)
   * 속성의 이름을 지정할 때 변수가 사용된 경우에 사용한다.
   * 정확하게 어떤 키가 필요한 지 모를 때, 즉 런타임에서 결정될 때 사용한다.

📌 객체가 갖고 있는 프로퍼티에 새로운 값을 할당하면 값은 갱신된다.

📌 객체가 갖고 있지 않은 프로퍼티에 값을 할당하면 주어진 키와 값으로 프로퍼티를 객체에 추가한다.

📌 `delete key값` 연산자를 이용하면 객체의 프로퍼티를 삭제할 수 있다.

<br />

## 객체 안에 함수 넣기
함수를 만들고 객체를 파라미터로 받아서 사용할 수 있다.
```jsx
const lightix = {
  name: 'kiwoong',
  age: 28,
  job: 'frontEndDeveloper'
};

const lvvrvsh = {
  name: 'seungsoo',
  age: 27,
  job: 'painter'
};

function print(person) {
  const introduction = `Hello. I'm ${person.age} years old and I'm ${person.job} ${person.name}.`;
  console.log(introduction);
}

print(lightix);
print(lvvrush);
```

<br />

## 객체 비구조화 할당 or 객체 구조 분해 (ES6)
```js
const object = { a: 1, b: 2};
const {a, b} = object;
console.log(a); // 1
console.log(b); // 2
```
```js
const object = { a: 1, b: 2 };

function print({a, b}) {
  console.log(a); // 1
  console.log(b); // 2
}

print(object);
```
print 함수에서 파라미터로 받아온 person의 값을 사용할 때마다 `person.`을 사용하는데, 객체 비구조화 할당을 이용해서 짧고 보기 좋게 작성할 수 있다.
```jsx
const lightix = {
  name: 'kiwoong',
  age: 28,
  job: 'frontEndDeveloper'
};

function print(person) {
  const {name, age, job} = person;
  const introduction = `Hello. I'm ${age} years old and I'm ${job} ${name}.`;
  console.log(introduction);
}

print(lightix);
```
같은 결과가 나오는 것을 볼 수 있다. 

더 축약한다면 매개변수로 `{name, age, job}` 을 사용할 수도 있다.

<br />

### 비구조화 할당에서 이름을 바꾸기
```js
const animal = {
  name: '멍멍이',
  type: '개'
}

const { name: nickname } = animal;
console.log(nickname); // 멍멍이
```
기존의 animal 객체가 바뀌는 것은 아니다

<br />

### 배열 비구조화 할당
```js
const array = [1, 2];
const [one, two] = array;

console.log(one); // 1
console.log(two); // 2
```

<br />

### 객체의 깊은 비구조화 할당
아래 객체에서 name, languages, value 값을 밖으로 꺼내고 싶다고 가정해보자.
```js
const deepObject = {
  state: {
    information: {
      name: 'ligntix',
      languages: ['html', 'css', 'javascript']
    }
  },
  value: 5
}
```
크게 두 가지 방법이 있다.

첫번째 방법은 비구조화 할당을 두번 사용하는 것이다.
```js
const { name, languages } = deepObject.state.information;
const { value } = deepObject;

const extracted = {
  name,
  languages,
  value
};

console.log(extracted);
```

두번째 방법은 비구조화 할당을 한번 사용해서 여러 값을 다 빼오는 것이다.

```js
const {
  state: {
    information: {
      name, languages
    }
  },
  value
} = deepObject;

console.log(extracted);
```
위 코드처럼 한번에 비구조화 할당을 사용하면 코드 가독성이 떨어지기 때문에, 비구조화 할당을 여러번에 걸쳐서 하는 것이 더 좋다.

<br />

## spread 문법(ES6)

### 객체에서 사용
spread 문법을 사용하면 객체나 배열을 펼칠 수 있다.
```js
const lightix = {
  name: 'kiwoong'
}

const cuteLightix = {
  name: 'kiwoong',
  attribute: 'cute'
}

const developerCuteLightix = {
  name: 'kiwoong',
  attribute: 'cute',
  job: 'developer'
}
```
위 코드처럼 기존의 객체를 참고해서 새로운 객체를 만들고 싶을 땐 spread 문법을 사용하면 된다.

```js
const lightix = {
  name: 'kiwoong'
}

const developerLightix = {
  ...lightix,
  job: 'developer'
}

const cuteDeveloperLightix = {
  ...developerLightix,
  attribute: 'cute'
}
```
해당 객체를 그대로 가져와서 사용하게 되는 것이다.

### 배열에서 사용
```js
const animals = ['개', '고양이', '참새'];
const anotherAnimals = [...animals, '오리'];
```

### 함수의 인자에서 사용
```js
function sum(a, b) {
  return a + b;
}

const numbers = [1, 2]
const result = sum(...numbers);

console.log(result); // 3
```
spread를 통해 배열의 모든 원소를 꺼내서 인자로 사용할 수 있다.
<br />

## rest 문법(ES6)
rest는 spread 문법과 생김새는 비슷하지만 역할이 다르다.
또한 rest는 객체, 배열 뿐 아니라 함수의 파라미터에서도 사용할 수 있다.

### 객체에서 사용
```js
const cuteDeveloperLightix = {
  name: 'kiwoong',
  job: 'developer',
  attribute: 'cute'
}

const { job, ...rest } = cuteDeveloperLightix;

console.log(job); // developer
console.log(rest); // Object {name: 'kiwoong', attribute: 'cute'}

const { attribute, ...lightix } = cuteLightix;
console.log(lightix); // Object {name: 'kiwoong'}
```
`...rest` 안에는 `job`을 제외한 객체가 들어가게 된다. 
> `...rest`는 예시일 뿐, `...cuteLightix` 등 맘대로 작성해도 된다.

spread는 특정 객체나 배열 안에 다른 객체나 배열을 퍼트리는 역할을 한다면, rest는 반대로 퍼져있는 것들을 모으는 역할을 한다.

### 배열에서 사용
```js
const numbers = [0, 1, 2, 3, 4, 5];
const [one, ...rest] = numbers;

console.log(one); // 0
console.log(rest); // [1, 2, 3, 4, 5]
```
주의할 점은 배열에서 rest는 항상 마지막에 와야한다.

### 함수의 파라미터에서 사용

함수의 파라미터로 몇 개를 받아올지 모르는 상황에서 입력된 값을 모두 더해주는 함수를 만든다고 가정해보자.
```js
function sum(a, b, c, d, e, f, g) {
  return a + b + c + d + e + f + g;
}

console.log(sum(1, 2, 3, 4, 5)); // NaN
```
파라미터의 개수보다 적게 입력할 경우 뒤에 오는 파라미터에 `undefined` 값이 들어가게 돼서 NaN이 나오게 된다.

해결 방법으로는 if문을 통해 해당 파라미터가 존재할 때만 더해주는 방법이 있지만, 코드가 지저분해지고 너무 길어지게 된다. 게다가 파라미터로 값을 더 넣게되면 코드를 또 추가해야 하기 때문에 권장되지 않는 방법이다.

이때 rest 문법을 사용하게 되면 간결하게 해결할 수 있다.
```js
function sum(...params) {
  return param.reduce( (acc, current) => {
    acc + current
  }, 0)
}

console.log(sum(1, 2, 3, 4, 5, 6, 7, 8));
```
`sum` 함수를 호출할 때 파라미터를 배열로 받아오게 된다. 이때 배열 내장함수인 `reduce`를 통해 모두 더해서 리턴해주면 해결된다.

```js
function sum(...params) {
  return param.reduce( (acc, current) => {
    acc + current
  }, 0)
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8];
console.log(sum(...numbers));
```
`spread`문법과 `rest`문법을 같이 사용하면 위 코드처럼 작성할 수 있다.

<br />

## This
함수가 객체안에 들어가면, `this`는 자신이 속해있는 객체를 가리킨다.

#### `this` 는 공부할 내용이 많아보이니 간단히만 알아보고, 이후에 작성할 [this](https://github.com/lightixxx/TIL/blob/master/JavaScript/learnMore/this.md)에서 자세히 다루자.

```jsx
const lightix = {
  name: 'kiwoong',
  age: '28',
  job: 'frontEndDeveloper',
  introduce: function() {
    console.log(`Hello. I'm ${this.age} years old and I'm ${this.job} ${this.name}.`)
  }
};

lightix.introduce();
```
📌 함수를 선언할 땐 이름이 없어도 된다.

📌 객체 안에 함수를 넣을 때, 화살표 함수로 선언하면 제대로 동작하지 않는다. (this가 뭔지 모르는 듯?)

<br />

**Q. 왜 객체는 const로 정의해도 값의 변경이 가능할까 ?**

> number, string, boolean, null, undefined 는 primitive 타입으로 값 자체가 레퍼런스에 저장된다. 반면에 객체는 레퍼런스가 const로 정의되었기 때문에 변경이 불가능 하지만, 레퍼런스가 가리키고 있는 값은 변경이 가능하다. [출처 - 드림코딩 엘리](https://youtu.be/1Lbr29tzAA8)

> object type을 객체 타입 또는 참조 타입이라 한다. 참조 타입이란 객체의 모든 연산이 실제값이 아닌 참조값으로 처리됨을 의미한다. 원시 타입은 값이 한번 정해지면 변경할 수 없지만(immutable), 객체는 프로퍼티를 변경, 추가, 삭제가 가능하므로 변경 가능(mutable)한 값이라 할 수 있다. 반면에 primitive 타입은 값으로 전달된다. 즉, 복사되어 전달되는데 이를 pass-by-value 라고 한다. [출처 - poiemaweb](https://poiemaweb.com/js-object)

자세한 내용은 아래 Pass-by-reference를 살펴보자.

<br />

### Pass-by-reference

```jsx
// Pass-by-reference
const foo = {
  val: 10
}

const bar = foo;
console.log(foo.val, bar.val); // 10 10
console.log(foo === bar); // true

bar.val = 20;
console.log(foo.val, bar.val); // 20 20
console.log(foo === bar); // true
```
`foo` 객체를 literal notation으로 생성하고, 상수 `foo` 는 객체 자체를 저장한 것이 아니라 생성된 객체의 참조값(address)를 저장하고 있다.

상수 `bar` 에 상수 `foo` 를 할당하고, 상수 `foo` 의 값은 생성된 객체를 가리키는 참조값이므로 상수 `bar` 에도 같은 참조값이 저장된다. 즉, `foo`,`bar` 모두 동일한 객체를 참조하고 있다. 따라서 참조하고 있는 객체의 `val` 값이 변경되면 상수 `foo`,`bar` 모두 변경된 객체의 프로퍼티 값을 참조하게 된다. 객체는 복사되는 것이 아니라 참조 방식으로 전달된다.

<br />

```jsx
const foo = { val: 10 };
const bar = { val: 10 };

console.log(foo.val, bar.val); // 10 10
console.log(foo === bar); // false

const baz = bar;

console.log(baz.val, bar.val); // 10 10
console.log(baz === bar) // true
```
`foo`와 `bar`의 내용은 같지만 참조값(address)는 동일하지 않다. 

`baz`에 `bar`의 값을 할당해서 동일한 객체를 가리키는 참조값을 저장했기 때문에 참조값은 동일하다.

```jsx
var a = { }, b = { }, c = { }; // 각각 다른 빈 객체를 참조
console.log(a === b, b === c, c === a); // false false false

a = b = c = {}; // 모두 같은 빈 객체를 참조
console.log(a === b, b === c, c === a); // true true true
```

<br />

### Pass-by-value
number, string, boolean, null, undefined, symbol과 같은 primitive type(원시 타입)은 값 자체가 복사되어 전달된다. 재할당은 가능하지만, 메모리 영역에서의 변경은 불가능하다.

```jsx
// Pass-by-value
const a = 1;
const b = a;

console.log(a, b); // 1 1
console.log(a === b); // true

a = 10;

console.log(a, b); // 10 1
console.log(a === b); // false
```

<br />

## Getter & Setter Function
객체 안에 Getter 함수와 Setter 함수를 설정해서 객체 안의 값을 수정할 수 있다.

```jsx
const numbers = {
  a: 1,
  b: 2
};

numbers.a = 5;
console.log(numbers); // {a: 5, b: 2}
```
<br>



Getter 함수와 Setter 함수를 사용하면, 값을 바꾸거나 값을 조회할 때 코드를 실행시킬 수 있다.

```jsx
const numbers = {
  a: 1,
  b: 2,
  get sum() {
    console.log('sum 함수 실행');
    return this.a + this.b;
  }
};

console.log(numbers.sum);
numbers.b = 5;
console.log(numbers.sum);
```

<br />

자바스크립트는 런타임 때 동적으로 타입이 결정되는 언어이기 때문에, 나중에 프로퍼티를 추가 및 삭제할 수 있다. 단, 유지보수 측면에서는 좋지 않은 습관이다.
```jsx
lightix.hasJob = false;
console.log(lightix.hasJob) // false

delete lightix.hasJob;
console.log(lightix.hasJob); // undefined
```

<br />


##### 출처

- [드림코딩 엘리](https://youtu.be/1Lbr29tzAA8)
- [poiemaweb](https://poiemaweb.com/js-object)