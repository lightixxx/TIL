# String
자바스크립트에서 가장 많이 사용하는 내장 객체 중 하나로 문자엻을 다룰 때 사용하는 내장객체이다. 변수 또는 객체의 프로퍼티가 값으로 문자열을 갖고 있으면 별도의 생성없이 프로퍼티와 메서드를 사용할 수 있다.

## 생성자 함수
```jsx
const lightix = new String('lightix');
console.log(lightix); // String {"lightix"} 0: "l" 1: "i" 2: "g" 3: "h" 4: "t" 5: "i" 6: "x" length: 7
```

`new` 연산자를 사용하지 않고 String 생성자 함수를 호출하면 String 객체가 아닌 문자열 리터럴을 반환한다.