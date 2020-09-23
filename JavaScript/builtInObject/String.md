# String
자바스크립트에서 가장 많이 사용하는 내장 객체 중 하나로 문자엻을 다룰 때 사용하는 내장객체이다. 변수 또는 객체의 프로퍼티가 값으로 문자열을 갖고 있으면 별도의 생성없이 프로퍼티와 메서드를 사용할 수 있다. String 객체가 전역객체로서 제공되기 때문에 스크립트 어디서든 사용할 수 있는 것이다. 또한, 문자열 자체가 마치 String 객체인 것 처럼 동작하기 때문에 래퍼 객체라고 부르기도 한다.

<br />

## Constructor
```jsx
const lightix = new String('lightix');
console.log(lightix); // String {"lightix"} 0: "l" 1: "i" 2: "g" 3: "h" 4: "t" 5: "i" 6: "x" length: 7
```

`new` 연산자를 사용하지 않고 String 생성자 함수를 호출하면 String 객체가 아닌 문자열 리터럴을 반환한다.
```jsx
const lightix = String('lightix');
console.log(typeof lightix, lightix); // string lightix
```

<br />

## Property

### String.length
문자열 내의 문자의 개수를 길이를 리턴한다. String 객체는 length 프로퍼티를 소유하고 있으므로 유사 배열 객체이다.
```jsx
const lightix = 'lightix';
console.log(lightix.length); // 7
```

<br />

## Method
String 객체의 메서드는 자기 자신을 변화시키지 않고 리턴한다.

<br />

### String.prototype.charAt(pos:number):string
인수로 전달한 인덱스를 사용해 해당하는 위치의 문자를 리턴한다.

인덱스는 0번부터 `length-1` 사이의 정수이다. 전달한 인덱스가 문자열 범위를 벗어나면 -1을 리턴한다.
```jsx
const lightix = 'lightix';
console.log(lightix.charAt(0)); // l
console.log(lightix.charAt(1)); // i
console.log(lightix.charAt(2)); // g
console.log(lightix.charAt(3)); // h
console.log(lightix.charAt(4)); // t
console.log(lightix.charAt(5)); // i
console.log(lightix.charAt(6)); // x
console.log(lightix.charAt(7)); // ''

// 문자열 순회
for(let i = 0; i < lightix.length; i++) {
  console.log(lightix.charAt(i));
}

// String 객체는 유사 배열 객체이므로 배열처럼 접근할 수도 있다.
for(let i = 0; i < lightix.length; i++) {
  console.log(lightix[i]);
}
```

<br />

### String.prototype.concat(...strings: string[]):string
인수로 전달한 문자열과 연결해서 새로운 문자열을 리턴한다.

단, concat 메서드를 사용하는 것 보다는 `+`,`+=` 같은 할당 연산자를 사용하는 것이 성능상 유리하다.

<br />

### String.prototype.indexOf(searchString, pos):number
인수로 전달한 문자 또는 문자열을 대상 문자열에서 검색해서, 처음 발견된 곳의 인덱스를 리턴한다. 발견하지 못하면 -1을 리턴한다.
```jsx
const lightix = 'lightix';

if(lightix.indexOf('ght') !== -1) {
  // 문자열 lightix에 'ght'가 포함된 경우 처리할 내용
}

//ES6에 추가
if(lightix.includes('ght')) {
  // 문자열 lightix에 'ght'가 포함된 경우 처리할 내용
}
```


<br />

```jsx
const lightix = 'Lightix'
```

|메서드|설명|예|결과|
|-----|-----------|--------|--------|
|`charAt()`|인덱스 번호를 인수로 전달받아 해당 위치의 문자를 리턴한다.|`lightix.charAt(4);`|`'t'`|
|`concat()`|인수로 전달한 문자열을 이어서 리턴한다.|`lightix.concat(' is handsome!');`|`"lightix is handsome!"`|
|`toUpperCase()`|문자열의 문자를 모두 대문자로 변경한다.|`lightix.toUpperCase();`|`'LIGHTIX'`|
|`toLowerCase()`|문자열의 문자를 모두 대문자로 변경한다.|`lightix.toLowerCase();`|`'lightix'`|
|`indexOf()`|문자열 내에서 지정된 문자 혹은 문자 집합이 처음으로 발견된 곳의 인덱스 번호를 리턴한다. 없으면 -1을 리턴한다.|`lightix.indexOf('ig');`|`1`|
|`lastIndexOf()`|문자열 내에서 지정된 문자 혹은 문자 집합이 마지막으로 발견된 곳의 인덱스 번호를 리턴한다.|`lightix.lastIndexOf('i')`|`5`|
|`substring()`|문자열 내에서 첫 번째 인덱스 번호에 해당하는 문자부터 두 번째 인덱스 번호에 해당하는 문자의 바로 이전 문자까지를 모두 리턴한다. 첫 번째 인덱스 번호에 해당하는 문자는 포함되지만, 두 번째 인덱스 번호에 해당하는 문자는 포함되지 않는다.|`lightix.substring(3, 5);`|`'ht'`|
|`split()`|지정된 문자가 나타날 때마다 문자열을 분리한 후, 분리된 각각의 문자열로 이루어진 배열을 만들어 리턴한다.|`lightix.split('i')`|`['l','ght','x']`|
|`trim()`|문자열의 양 끝에 있는 공백 문자를 제거한 후 리턴한다.|`lightix.trim();`|`'lightix'`|
|`replace()`|찾아 바꾸기 기능처럼 첫 번째 인수로 지정된 문자열을 대상 문자열에서 찾아 두 번째 인수로 지정된 문자열로 대체한다. 기본적으로 이 동작은 첫 번째 인수로 지정된 문자열을 처음 발견했을 때 한 번만 실행된다.|`lightix.replace('i','❗️')`|`'l❗️ghtix'`|