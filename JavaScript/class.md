# class

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