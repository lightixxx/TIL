# class
ES6에 추가된 객체를 만들 수 있는 새로운 방법이다.

```jsx
// 선언적 방식
class A {}
console.log(new A());

// 표현식을 변수에 할당
class B = class {};
console.log(new B());
```
클래스는 클래스 선언문 이전에 참조할 수 없다. 하지만 호이스팅이 아예 발생하지 않는 것은 아니라 `let`, `const` 키워드로 선언한 변수처럼 호이스팅이 된다. 따라서 클래스 선언문 이전에 일시적 사각지대(Temporal Dead Zone, TDZ)에 빠지기 때문에 호이스팅이 발생하지 않는 것처럼 동작한다.

<br />

## class 선언
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

### constructor
함수를 통해 객체를 만들 때 함수에 인자로 넣어서 외부에서 객체를 생성할 때 안으로 넣어줄 수 있는 것처럼 클래스에서도 `constructor`로 사용할 수 있다. 객체가 생성될 때 실행되는 함수이다(?)

- `constructor`는 인스턴스를 생성하고 클래스 필드를 초기화하기 위한 특수한 메서드이다.
- `constructor`는 클래스 내에 한 개만 존재할 수 있다.
- `constructor`의 파라미터에 전달한 값은 클래스 필드에 할당한다.

<br />

### class field
클래스 내부의 캡슐화된 변수를 말한다. 멤버 변수라고도 부르며 클래스 필드는 인스턴스의 프로퍼티 또는 정적 프로퍼티가 될 수 있다. 생성자 함수에서 `this`에 추가한 프로퍼티를 클래스 필드라고 이해하면 된다.

클래스 몸체에는 메서드만 선언할 수 있다. 클래스 바디에 클래스 필드(멤버 변수)를 선언하면 에러가 발생한다.

<br />

## Getter & Setter
클래스를 사용하는 사용자가 잘못 사용해도 방어적인 자세로 만들어 주는 것
```jsx
class User {
	constructor(firstName, lastName, age) {
		this.firstName = firstName;
		this.lastName = lastName;
		this.age = age;
	}
}

const user1 = new User('Kiwoong', 'lee', -1);
console.log(user1.age); // 사용자의 나이가 -1인 것은 말이 안된다
```

- `get`을 이용해서 값을 리턴한다.
- `set`을 이용해서 값을 설정한다. 단(value)를 받아와야 한다.

```jsx
class User {
	constructor(firstName, lastName, age) {
		this.firstName = firstName;
		this.lastName = lastName;
		this.age = age;
	}

	get age() {
		return this._age;
	}
	
	set age(value) {
		//if (value < 0) {
		//	throw Error('age can not be negative');
		//}
		this._age = value < 0 ? 0 : value;
	}
}

const user1 = new User('Kiwoong', 'lee', -1);
console.log(user1.age);
```
age라는 getter를 정의하는 순간 this.age는 메모리에 올라가있는 데이터를 읽어오는 것이 아니라 getter를 호출하게 된다.

그리고 age라는 setter를 정의하는 순간 '= age'로 값을 할당할 때, 바로 메모리에 값을 할당하는 것이 아니라 setter를 호출하게 된다.

곧 setter 안에서 전달된 value를 this.age에 할당할 때, 메모리에 값을 업데이트하는 것이 아니라 setter를 호출하게 된다. 

따라서 세터를 무한 호출하는 것을 방지하기 위해 getter와 setter안에서 쓰여지는 변수의 이름을 this._age처럼 다르게 만들어야한다.




##### 출처
- [poiemaWeb](https://poiemaweb.com/es6-class)
- fastcampus 온라인강의