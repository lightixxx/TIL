# Constructor function (생성자 함수)

new 키워드로 객체를 생성할 수 있는 함수를 의미한다.

<br />

## 📌 여기서 꼭 알아야 할 용어
- instance : 생성자 함수를 기반으로 생성한 객체를 말한다.
- prototype : 생성자 함수로 생성한 객체들이 공동으로 갖는 공간을 말한다. 보통 메서드를 선언한다.

<br/>

### 생성자 함수를 이용하여 새로운 객체를 만들어 내는 방법
   
```jsx
function Person(name, age) {
	this.name = name;
	this.age = age;
}

const lightix = new Person('lightix', 28);
```

<br />

### 함수를 호출하면 함수를 만들어서 리턴하는 방법
```jsx
function plus(base) {
	return function(num) {
		return base + num;
	}
}

const plus5 = plus(5);
console.log(plus5(10)); // 15
```

<br />

### 함수를 호출할 때, 인자로 함수를 사용하는 방법

```jsx
function hello(callback) {
	console.log('hello');
	callback();
}

hello(() => {
	console.log('콜백함수');
});
```

<br />

📌 화살표 함수로는 함수 안에 this가 생기지 않기 때문에 생성자 함수를 만들 수 없다.

📌 생성자 함수의 이름은 관례적으로 대문자로 시작한다.

📌 프로퍼티 또는 메소드 앞에 작성된 `this`는 생성자 함수가 생성할 인스턴스를 가리킨다.

📌 `this`에 연결되어 있는 프로퍼티와 메소드는 외부에서 참조 가능하다.

📌 생성자 함수 내에서 선언된 일반 변수는 외부에서 참조가 불가능하다. 즉 생성자 함수 내부에서는 자유로운 접근이 가능하지만, 외부에서는 접근할 수 없다.

<br />

### Student 생성자 함수 만들기
1. 생성된 객체는 이름, 국어, 수학, 영어 속성을 작성한다.
2. 모두 더하는 메서드, 평균을 구하는 메서드를 작성한다.
3. 학생들의 총점과 평균을 출력한다.

```jsx
function Student(name, kor, math, eng) {
  // 속성
  this.name = name;
  this.kor = kor;
  this.math = math;
  this.eng = eng;

  // 메서드
  this.getSum = function() {
    return this.kor + this.math + this.eng;
  };

  this.getAverage = function() {
    return this.getSum() / 3;
  };

  this.toString = function() {
    return this.name + '\t' + this.getSum() + '\t' + this.getAverage();
  };
}

  // 학생의 정보를 담을 배열을 만든다.
  let students = [];
  students.push(new Student('lightix', 90, 92, 95));
  students.push(new Student('gildong', 95, 70, 93));
  students.push(new Student('amoogae', 63, 74, 89));
  students.push(new Student('mollang', 86, 21, 87));
  students.push(new Student('babo', 64, 39, 28));

  // 출력한다
  let output = '이름\t총점\t\평균\n';
  for(let i in students) {
    output += students[i].toString() + '\n';
  }
  console.log(output);
```
##### `Student()` 함수는 `new` 키워드로 객체를 생성하므로 생성자 함수이다. 그리고 `Student` 생성자 함수로 만든 객체 `student`를 <u>객체</u> 또는 <u>인스턴스</u>라고 부른다.

<br />

##### 코드를 실행하면 각각 학생의 총점과 평균을 출력한다. 그냥 함수로 객체를 리턴하는 방법과 차이가 없어 보인다. 이후 나오는 프로토타입을 배우면 이해가 된다.

<br />

### instanceof 연산자

인스턴스가 어떤 생성자 함수로 생성됐는지 확인할 땐, instanceof 키워드를 사용한다.
```jsx
function Student() {...}
const lightix = new Student();

console.log(lightix instanceof Student); // true
console.log(lightix instanceof Object); // true
```

<br />

## Prototype
생성자 함수로 생성한 객체들이 공동으로 갖는 공간을 말한다. 일반적으로 메서드를 이런 공간에 선언한다.
- ES6에서 클래스가 추가되었으므로 간단하게만 살펴보자.
- Prototype 객체는 생성자 함수에 의해 생성된 각각의 객체에 공유 프로퍼티를 제공하기 위해서 사용한다.

> 자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있다. 마치 객체 지향의 상속 개념과 같이 부모 객체의 프로퍼티 또는 메소드를 상속받아 사용할 수 있게한다. 이런 부모 객체를 `Prototype`이라고 한다. [출처 -poiemaweb](https://poiemaweb.com/js-prototype)

생성자 함수로 생성된 객체의 속성은 각각 다른 값을 갖지만 메서드는 모두 같은 값을 갖는 경우가 많다. 각 객체를 생성할 때마다 동일한 함수를 계속 생성하는 것은 메모리를 쓸데없이 잡아먹는 비효율적인 일이다. 이런 문제를 해결해기 위해 자바스크립트는 프로토타입 공간을 만들었다.

메서드를 하나만 생성해도 모든 객체가 해당 메서드를 사용할 수 있기 때문에 생성자 함수로 객체를 만들 때는 생성자 함수 내부에 속성만 넣어 주고, 메서드는 모두 프로토 타입 안에 따로 넣어준다.
```jsx
function Student(name, kor, math, eng) {
  this.name = name;
  this.kor = kor;
  this.math = math;
  this.eng = eng;

  Student.prototype.getSum = function() {
    return this.kor + this.math + this.eng;
  }

  Student.prototype.getAverage = function() {
    return this.getSum() / 3;
  }

  Student.prototype.toString = function() {
    return this.name + '\t' + this.getSum() + '\t' + this.getAverage();
  }

}
let students = [];
const lightix = new Student('lightix', 30, 50, 40);

students.push(lightix);

let output = '이름 \t 총점 \t 평균 \n';
for(let i in students) {
    output += students[i].toString() + '\n';
  }
  console.log(output);
```


<br />

## class (ES6)
현대 프로그래밍 언어를 지배하는 '객체지향'이라는 이념은 크게 두가지 방법으로 구분된다.
- 클래스 기반 객체지향 언어: C++, C#, 자바, 파이썬, 루비 등
- 프로토타입 기반 객체지향 언어: 자바스크립트, 루아

많이 사용되는 프로그래밍 언어는 대부분 클래스 기반의 객체지향 언어이다. 이런 흐름에 맞춰서 자바스크립트에서도 ES6 부터 '클래스 기반의 객체지향 언어' 이념을 도입했다. 
> 호환성을 위해 클래스 형태로 작성하면 이를 내부에서 생성자 함수로 구현하는 것과 같게 변환한다. 따라서 다른 클래스 기반의 객체지향 언어가 갖고 있는 모든 특성을 구현하지는 못한다.

만약 객체나 클래스가 없다면 정의한 변수들이 여기저기 흩어져서 규모있는 프로젝트를 진행하기 어려울 것이다. 클래스는 조금 더 연관있는 데이터를 한 곳에 묶어놓는 컨테이너 같은 것이라고 생각하면 편하다. 기존의 프로토타입을 기반으로 문법만 간단하게 추가된 형태이다.

<br />

### class 선언
```jsx
class Person {
	// constructor
	constructor(name, age) {
		// fields
		this.name = name;
		this.age = age;
	}

	// methods
	speak() {
		console.log(`${this.name}: hello!`);
	}
}

// 새로운 키워드를 만들때는 new 키워드를 사용한다
const lightix = new Person('lightix', '28');

console.log(lghtix.name); // lightix
console.log(lghtix.age); // 28
lightix.speak(); // ligthix: hello!
```
<br />



### 상속
상속은 기존의 생성자 함수나 객체를 기반으로 새로운 생성자 함수나 객체를 쉽게 만드는 것을 말한다. 기존의 객체를 기반으로 생성하므로 상속으로 새로 만들어지는 객체에는 기존 객체의 특성이 모두 들어있다.
- 기존의 객체에서 속성과 메서드를 물려받는 것과 비슷하다고 해서 상속이라는 이름을 사용한다.
- 상속을 이용하면 기존에 만들었던 객체와 비슷한 객체를 쉽게 생성할 수 있다.


<br />
<br />
<br />

### 연습문제

<br />

다음과 같은 객체를 생성할 수 있는 생성자 함수를 예로 들어보세요.

|속성|값|
|-----|-----|
|이름|돼지삼겹살|
|무게|100g|
|가격|1690원|

<br />

|메서드|설명|
|-----|---------|
|calculate()|무게를 기반으로 가격을 계산한다.|

<br />

```jsx
function Product(name, weight, price){
  this.name = name;
  this.weight = weight;
  this.price = price;

  this.calculate = function(weight) {
    return `${this.name} ${this.weight}g은 총 ${this.price * (this.weight / 100)}원 입니다.`
  }
}
const product = new Product('돼지삼겹살', 100, 1690);
console.log(product.calculate());
```