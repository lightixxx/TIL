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

📌 인스턴스가 어떤 생성자 함수로 생성됐는지 확인할 땐, instanceof 키워드를 사용한다.

<br />

## Prototype
생성자 함수로 생성된 객체가 공통으로 가지는 공간.
