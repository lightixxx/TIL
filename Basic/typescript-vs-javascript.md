# Typescript vs Javascript

## TypeScript란?

JavaScript는 오류가 많고 후졌지만, JavaScript가 실행되는 웹이 워낙에 빠르게 발전했고, 세상에 이롭게 작용했기 때문에 살아남은 언어이다. 또한 ES2015버전 이후로는 굉장히 쓸만한 프로그래밍 언어가 되었다.

보통 'JavaScript는 TypeScript의 슈퍼 셋'이라고 말한다. 슈퍼 셋은 기본적으로 하위 호환성을 지원한다고 표현할 수 있는데, TypeScript는 JavaScript의 모든 기능을 기본으로 다 제공한다. 거기에 더해서 추가 기능을 제공한다는 의미에서 슈퍼 셋이라고 부른다.

<br />

## 유형(Type) 정의

Type은 유형이라고 해석할 수 있는데, JavaScript가 제공하지 못하는 것, 앞으로도 제공하지 못 할 것을 제공한다. 명시적인 유형 설명 즉, 데이터에 대한 설명이라고 하는 기능을 제공한다. 이를 통해 JavaScript와 TypeScript가 공생의 전략을 취하게 된다. 결국 TypeScript를 배운다는 것은 JavaScript를 배운 다는 것과 일맥상통하고 플러스 알파를 더 배운다고 생각할 수 있다. 입문자들에겐 JavaScript 보다 TypeScript를 먼저 배우게 되면 이해가 어려울 수 있다. 먼저 JavaScript를 배우고 거기에 TypeScript가 제공하는 기능을 추가로 학습하는 것이 더 효과적일 것이다.

<br />

## 실습

데이터를 설명하는 기능이 없는 것과 있는 것의 차이, 그리고 어떻게 데이터에 설명을 붙이는지에 대해 알아보겠다. 프로그래밍 언어에선 데이터를 설명할 때 보통 변수를 사용한다.

나이라는 데이터를 만들어보자.

```js
let age = 30
```

변수 age는 이름으로써 30이라는 데이터를 설명하고 있다. age라고 하는 설명, 데이터의 설명은 결국 30이라는 것을 설명하는 것이다. 즉 '30살'이라고 예측할 수 있다.

```js
let x = 30
```

다른 예로 x에 30을 넣게되면 30이 어떤 의미를 갖고 있는지 알 수 없다.

<br />

```js
let weight = 70
```

어딘가에서 weight를 쓰는 상황이 생기면 이 weight라고 하는 값이 JavaScript에서는 '무게'로 해석할 수 있을텐데, 무게에 들어가 있는 값이 숫자인지, 문자인지 혹은 다른 유형의 값인지는 알 수 없다. 왜냐하면 JavaScript 코드에선 그걸 설명해 주지 않기 때문이다. 단순히 의미만 알 수 있다.

이 부분을 TypeScript가 제공해주고 있다.

```ts
let weight: number = 70
```

훨씬 더 명시적이고 명확하게 데이터를 설명하는 것을 알 수 있다. 이게 바로 TypeScript가 제공하는 데이터의 유형 설명 기능이다.

<br />

#### 출처

- [패스트캠퍼스 JavaScript & TypeScript Essential](https://fastcampus.co.kr/dev_academy_kmt1)
