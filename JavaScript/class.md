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
