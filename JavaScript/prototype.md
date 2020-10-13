# Prototype 객체
자바스크립트는 기본적으로 프로토타입 기반 객체지향 프로그래밍 언어이다. 자바스크립트의 동작원리를 이해하기 위해서는 프로토타입의 개념을 잘 이해해야 한다!

자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있다. 마치 객체 지향의 상속개념과 같이 부모 객체의 프로퍼티 혹은 메서드를 상속받아 사용할 수 있게 한다. 이런 부모 객체를 **Prototype 객체**라고 한다.

또한 프로토타입 객체는 생성자 함수에 의해 생성된 각각의 객체에 공유 프로퍼티를 제공하기 위해 사용한다.

<br />

## [[Prototype]] 과 prototype 프로퍼티
자바스크립트에서 모든 객체는 자신의 프로토타입 객체를 가리키는 [[Prototype]]을 갖고, 상속을 위해 사용된다. 함수도 객체이기 때문에 마찬가지로 [[Prototype]]을 갖는다.

하지만 함수객체는 일반 객체와는 다르게 prototype 프로퍼티도 갖는다.

<br />

### [[Prototype]]
- 함수를 포함한 모든 객체가 갖고 있는 인터널 슬롯(내부 속성)이다.
- 객체의 입장에서 자신의 부모인 프로토타입 객체를 가리키며, 함수객체의 경우 `Function.prototype`을 가리킨다.

### prototype 프로퍼티
- 함수 객체만 갖고있는 프로퍼티이다.
- 함수 객체가 생성자로 사용될 때, 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체(프로토타입 객체)를 가리킨다.


<br />

## constructor 프로퍼티
프로토타입 객체는 constructor 프로퍼티를 갖는다. 이 프로퍼티는 객체의 입장에서 자신을 생성한 객체를 가리킨다.


<br />

## prototype chain
특정 객체의 프로퍼티나 메서드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티나 메서드가 없다면 [[Prototype]]이 가리키는 링크를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메서드를 차례대로 검색한다. 그것을 **프로토타입 체인**이라고 한다.
```jsx
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.hello = function () {
    console.log('hello', this.name, this.age);
  };
}

const p = new Person('Lightix', 28);
p.hello(); // Hello Lightix 28
console.log(p.toString()); // [Object Object]

console.log(Person.prototype); // Person { }
console.log(Person.prototype.toString; // [Function: toStriong]
console.log(Person.prototype.constructor // [Function: Person]
console.log(Person.hello); // undefined
console.log(Person.prototype.hello); // undefined
```

<br />

## 프로토타입을 이용한 객체 확장
```jsx
function Person() {}

Person.prototype.hello = function() {
  console.log('hello');
}

function Korean(region) {
  this.region = region;
  this.where = function() {
    console.log('where', this.region);
  };
}

Korean.prototype = Person.prototype;

const k = new Korean('Seoul');

k.hello(); // hello
k.where(); // hello Seoul

console.log(k instanceof Korean); // true
console.log(k instanceof Person); // true
console.log(k instanceof Object); // true
```
`prototype`을 활용해서 부모의 객체를 자식의 객체 어딘가에 프로퍼티로 할당할 수 있다.


##### 출처
- [poiemaWeb](https://poiemaweb.com/js-prototype)
- fastcampus 온라인강의