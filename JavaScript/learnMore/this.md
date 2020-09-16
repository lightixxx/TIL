# this
함수가 호출될 때, 매개변수로 전달되는 인자값 외에 `arguments`객체 와 `this`를 암묵적으로 전달받는다.
- 자바스크립트는 `this`에 바인딩되는 객체는 한 가지가 아니라 해당 함수의 호출 방식에 따라 `this`에 바인딩 되는 객체가 달라진다.

```jsx
function square(num) {
  console.log(arguments);
  console.log(this);

  return num * num;
}

square(2);
```

## 함수 호출 방식과 this 바인딩
자바스크립트는 함수 호출 방식에 의해 `this`에 어떤 객체가 바인딩될지 동적으로 결정된다. 즉, 함수를 선언할 때 `this`에 바인딩할 객체가 정적으로 정해지는 것이 아니라, 함수를 호출할 때 함수가 어떻게 호출되는지에 따라 `this`에 바인딩할 객체가 동적으로 결정된다.

> 스코프에서 배웠던 정적(렉시컬) 스코프는 함수를 선언할 때 결정되고, `this`는 함수가 호출될 때 결정된다.

<br />

## this 요약

* 기본적으로 `this`는 전역객체에 바인딩된다.
* 전역함수, 내부함수도 전역객체에 바인딩된다.
* 메서드의 내부함수도 전역객체에 바인딩된다.
* 콜백함수도 전역객체에 바인딩된다.
* 메서드 내부의 `this`는 호출한 객체에 바인딩된다.
* 프로토타입 객체 메서드 내부에 사용된 `this`는 호출한 객체에 바인딩된다.
* `new`연산자와 함께 생성자 함수를 호출하면 `this`는 생성된 인스턴스에 바인딩된다.

<br />

```jsx
var foo = function () {
  console.dir(this);
};

// 1. 함수로 호출
foo(); // window.foo()

// 2. 메소드로 호출
var obj = { foo: foo };
obj.foo(); // obj

// 3. new 호출
var instance = new foo(); // instance

// 4. apply / call / bind 호출
var bar = { name: 'lightix' };
foo.apply(bar); // bar
foo.call(bar); // bar
foo.bind(bar)(); // bar
```

<br />

## 함수로 호출
전역 객체는 모든 객체의 유일한 최상위 객체를 의미한다.
Browser-side 에서는 `window`, Server-side(Node.js)에서는 `global` 객체를 의미한다.

전역 객체는 전역 변수를 프로퍼티로 소유한다. 전역에 선언한 함수또한 전역 객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드이다.

```jsx
var global = 'Global variable';

console.log(global == window.global) // true

function foo() {
  console.log('hello world');
}
window.foo();
```
<br />

`this`는 전역객체에 바인딩된다. 전역함수와 내부함수도 전역객체에 바인딩 된다.

```jsx
function outerFunc() {
  console.log("outerFunc's this: ", this); // window
  function innerFunc() {
    console.log("innerFunc's this: ", this); // window
  }
  innerFunc();
}
outerFunc();
```
<br />

메소드의 내부함수도 `this`는 전역객체에 바인딩된다.
```jsx
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar() {
      console.log("bar's this: ",  this); // window
      console.log("bar's this.value: ", this.value); // 1
    }
    bar();
  }
};

obj.foo();
```
<br />

콜백함수도 전역객체에 바인딩된다.

```jsx
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    setTimeout(function() {
      console.log("callback's this: ",  this);  // window
      console.log("callback's this.value: ",  this.value); // 1
    }, 100);
  }
};

obj.foo();
```



전역객체에 바인딩되는 것을 회피하는 방법은 다음과 같다.
```jsx
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    var that = this;  // Workaround : this === obj

    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar() {
      console.log("bar's this: ",  this); // window
      console.log("bar's this.value: ", this.value); // 1

      console.log("bar's that: ",  that); // obj
      console.log("bar's that.value: ", that.value); // 100
    }
    bar();
  }
};

obj.foo();
```
이 방법 외에도 `this`를 명시적으로 바인딩할 수 있는 `apply`, `call`, `bind` 메서드가 있다. 마지막에 알아보자.

## 메서드로 호출
메서드 내부의 `this`는 해당 메서드를 호출한 객체에 바인딩된다.

```jsx
var obj1 = {
  name: 'lightix',
  sayName: function() {
    console.log(this.name);
  }
}

var obj2 = {
  name: 'lvvrvsh'
}

obj2.sayName = obj1.sayName;

obj1.sayName(); // 'lightix'
obj2.sayName(); // 'lvvrvsh'
```
<br />

프로토타입 객체 메서드 내부에서 사용된 `this`도 호출한 객체에 바인딩된다.

```jsx
function Person(name) {
  this.name = name;
}

Person.prototype.getName = function() {
  return this.name;
}

var me = new Person('Lee');
console.log(me.getName());

Person.prototype.name = 'Kim';
console.log(Person.prototype.getName());
```
<br />

## 생성자 함수 호출
일반 함수를 호출하게되면 `this`는 전역객체에 바인딩되지만, `new`연산자와 함께 생성자 함수를 호출하면 `this`는 생성자 함수가 생성한 인스턴스에 바인딩된다.
```jsx
function Person(name) {
  // new없이 호출하는 경우, 전역객체에 name 프로퍼티를 추가한다.
  this.name = name;
};

// 일반 함수로서 호출되었기 때문에 객체를 암묵적으로 생성하여 반환하지 않는다.
// 일반 함수의 this는 전역객체를 가리킨다.
var me = Person('Lee');

console.log(me); // undefined
console.log(window.name); // Lee
```
생성자 함수를 new 없이 호출한 경우, 함수 Person 내부의 this는 전역객체를 가리키므로 name은 전역변수(window)에 바인딩된다. 또한 new와 함께 생성자 함수를 호출하는 경우에 암묵적으로 반환하던 this도 반환하지 않으며, 반환문이 없으므로 undefined를 반환하게 된다.

<br />

## apply / call / bind 호출

### apply( )
```jsx
func.apply(thisArg, [argsArray]);
// thisArg: 함수 내부의 this에 바인딩할 객체
// argsArray: 함수에 전달할 argument의 배열
```

`apply()` 메서드는 `this`를 특정 객체에 바인딩하는 메서드이지만 본질적인 기능은 함수 호출이다.

```jsx
var Person = function (name) {
  this.name = name;
};

var foo = {};

// apply 메소드는 생성자함수 Person을 호출한다. 이때 this에 객체 foo를 바인딩한다.
Person.apply(foo, ['name']);

console.log(foo); // { name: 'name' }
```
`apply()` 메서드의 첫번째 매개변수에 빈 객체 `foo`를 전달하고, 두번째 매개변수에 argument의 배열을 전달하면서 `Person`함수를 호출했다.

여기서 `Person` 함수의 `this` 는 `foo` 객체가 된다. 

`Person`함수는 `this`의 `name` 프로퍼티에 매개변수 `name`에 할당된 인수를 할당하는데, `this`에 바인딩된 `foo`객체에는 `name` 프로퍼티가 없기 때문에, 동적으로 `name` 프로퍼티를 추가하고 값을 할당한다.

<br />

`apply()` 메서드의 대표적인 용도는 arguments 객체와 같은 유사 배열 객체에 배열 메서드를 사용하는 경우이다. arguments 객체는 배열이 아니기 때문에 배열의 메서드를 사용할 수 없지만, `apply()` 메서드를 이용하면 가능하다.

<br />

### call( )
`apply()`와 기능은 같지만, `apply()`의 두번째 인자에서 배열 형태로 넘긴 것을 각각 하나의 인자로 넘긴다.
```jsx
Person.apply(foo, [1, 2, 3]);
Person.call(foo, 1, 2, 3);
```
`apply()`와 `call()` 메서드는 콜백함수의 this를 위해 사용되기도 한다.

```jsx
function Person(name) {
  this.name = name;
}

Person.prototype.doSomething = function(callback) {
  if(typeof callback == 'function') {
    // --------- 1
    callback();
  }
};

function foo() {
  console.log(this.name); // --------- 2
}

var p = new Person('Lee');
p.doSomething(foo);  // undefined
```
1번 시점에서 `this`는 `Person`객체를 가리키고, 2번 시점에서는 `window`전역객체를 가리킨다. 콜백함수를 호출하는 외부 함수 내부의 `this`와 콜백함수 내부의 `this`가 다르기 때문에 문제가 발생한다. 따라서 콜백함수 내부의 `this`를 콜백함수를 호출하는 함수 내부의 `this`와 일치시켜 주어야하는 번거로움이 생긴다.

```jsx
function Person(name) {
  this.name = name;
}

Person.prototype.doSomething = function (callback) {
  if (typeof callback == 'function') {
    callback.call(this); // !
  }
};

function foo() {
  console.log(this.name);
}

var p = new Person('Lee');
p.doSomething(foo);  // 'Lee'
```
<br />

### bind( ) (ES5)
`Function.prototype.bind`는 함수에 인자로 전달한 `this`가 바인딩된 새로운 함수를 리턴한다. 즉, `Function.prototype.bind`는 `Function.prototype.apply`와 `Function.prototype.call` 메서드처럼 함수를 실행하지 않기 때문에 함수를 호출해줄 필요가 있다.

```jsx
function Person(name) {
  this.name = name;
}

Person.prototype.doSomething = function (callback) {
  if (typeof callback == 'function') {
    // callback.call(this);
    // this가 바인딩된 새로운 함수를 호출
    callback.bind(this)(); // !
  }
};

function foo() {
  console.log('#', this.name);
}

var p = new Person('Lee');
p.doSomething(foo);  // 'Lee'
```

<br />

출처 - [poiemaweb](https://poiemaweb.com/js-this)