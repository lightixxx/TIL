# Asynchronous(비동기적)

작업을 동기적으로 처리한다면 작업이 끝날 때까지 기다리는 동안 다른 작업은 중지된다. 이때 비동기적으로 처리를 하면 기다리지 않고 여러 작업을 동시에 처리할 수 있다.

```js
function work() {
  const start = Date.now();
  for (let i = 0; i < 1000000000; i++) { }
  const end = Date.now();
  console.log(end - start + 'ms');
}

work();
console.log('다음 작업')
```
위 `work`함수는 1,000,000,000번 루프를 돌고 이 작업이 얼마나 걸렸는지 알려주는 함수이다. 이 함수가 호출이 되면 for문은 다른 작업은 처리하지 않고, 루프가 끝난 뒤에야 비로소 `console.log('다음 작업')`을 실행한다. 

> 결과 : 508ms -> 다음 작업

만약 위 상황에서 루프가 도는 동안 다른 작업도 하고싶다면 함수를 비동기 형태로 전환해주어야 한다.

```js
function work() {
  setTimeout( () => {
    const start = Date.now();
    for(let i = 0; i < 1000000000; i++) {}
    const end = Date.now();
    console.log(end - start + 'ms')
  }, 0)
}

console.log('작업 시작')
work();
console.log('다음 작업')
```

`setTimeout`함수는 첫번째 파라미터에 넣은 함수를 두번째 파라미터에 넣은 시간이 흐른 뒤에 호출한다. 이렇게 `setTimeout`을 사용하면 작업이 백그라운드에서 수행되기 때문에 기존의 코드 흐름을 막지 않고 동시에 다른 작업들을 진행할 수 있다.

> 결과 : 작업 시작 -> 다음 작업 -> 508ms

결과를 보면, 작업이 시작되고 for 루프가 돌아가는 동안 다음 작업을 실행하고, for 루프가 끝나면 결과를 알려준다.

만약 `work` 함수가 끝난 다음에 어떤 작업을 처리하고 싶다면 callback 함수를 파라미터로 전달하면 된다.

```js
function work(callback) {
  setTimeout(() => {
    const start = Date.now();
    for(let i = 0; i < 1000000000; i++) {}
    const end = Date.now();
    console.log(end - start + 'ms');
    callback();
  }, 0)
}

console.log('작업 시작');
work(() => {
  console.log('작업 끝!')
});
console.log('다음 작업');
```

> 결과 : 작업 시작 -> 다음 작업 -> 508ms -> 작업 끝!


- Ajax Web API 요청 : 서버쪽에서 데이터를 받아올 때, 요청을 하고 서버에서 응답할 때까지 대기를 해야하기 때문에 작업을 비동기적으로 처리한다.
- 파일 읽기 : 서버 쪽에서 파일을 읽어야 하는 상황에는 비동기적으로 처리한다.
- 암호화/복호화 : 암호화/복호화를 할 때에도 바로 처리가 되지 안혹, 시간이 어느정도 걸리기 때문에 비동기적으로 처리한다.
- 작업 예약 : 단순히 어떤 작업을 몇 초 후에 스케쥴링 해야하는 상황에서 `setTimeout`을 사용해서 비동기적으로 처리를 한다.

<br />

## async function
Promise를 기반으로 AsyncFunction 객체를 반환하는 하나의 비동기 함수를 정의한다.

<br />

### Promise 객체가 resolve 될 때 async
```jsx
// Promise 객체를 리턴하는 함수
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

// Promise 객체를 이용해서 비동기 로직을 수행할 때
p(1000).then(ms => {
  console.log(`${ms} ms 후에 실행된다.`);
});

// Promise 객체를 리턴하는 함수를 await로 호출하는 방법
async function main() {
  const ms = await p(1000);
  console.log(`${ms} ms 후에 실행된다.`);
}

main();
```
`then`으로 연결해서 가지 않고, 앞에 `await` 키워드를 붙이면 resolve 됐을 때, ms가 리턴값으로 온다. `await`처리를 하게되면 실제로는 비동기 처리를 보냈지만, 비동기 처리가 끝날 때 까지 다음 코드로 넘어가지 않고 기다렸다가 resolve가 되면 넣어준 인자 값을 return해서 다음 코드로 넘어가게 된다.

`await`는 오직 async function 안에서만 유효하기 때문에 async function 으로 감싸준다.

<br />

### Promise 객체가 reject 될 때 async
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(new Error('reason'));
    }, ms);
  });
}

// try catch를 이용한다.
async function main() {
  try {
    const ms = await p(1000);
  } catch (error) {
    console.log(error);
  }
}

main();
```
resolve됐을 땐 try 구문에서 실행되고, reject 됐을 땐 `catch`로 인자가 넘어오게 된다.

<br />

### Promise 없이 async function 에서 
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(new Error('reason'));
    }, ms);
  });
}

async function asyncP() {
  return 'lightix'; // 값이 리턴되면 바로 resolve 된다
}

async function main() {
  try {
    const name = await asyncP();
    console.log(name);
  } catch (error) {
    console.log(error);
  }
}

main();
```
이렇게 되면 `asyncP`는 resolve만 되기 때문에 `catch`구문 까지 가지않고 `name`을 바로 리턴한다.

<br />

### async function 에서 return되는 값은 Promise.resolve 함수로 감싸서 리턴된다.
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

async function asyncP() {
  const ms = await p(1000);
  return 'lightix' + ms;
}

async function main() {
  try {
    const name = await asyncP();
    console.log(name);
  } catch (error) {
    console.log(error);
  }
}

main();
```
`asyncP`로 갔다가 `p`로 가서 resolve될 때 까지 기다렸다가 resolve된 다음에 리턴이 된다. `p`를 통해 얻어온 값을 통해서 다른 작업을 한 다음에 main 함수에 돌려주는 식으로 사용이 가능해진다.

<br />

### error의 전파
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(new Error('reason'))
    }, ms);
  });
}

async function asyncP() {
  const ms = await p(1000);
  return 'lightix' + ms;
}

async function main() {
  try {
    const name = await asyncP();
    console.log(name);
  } catch (error) {
    console.log(error);
  }
}

main();
```
reject의 경우 `asyncP`로 가서 `p`를 호출할 때 1초 기다렸다가 reject가 불리면서 error가 throw된다.

`main`에서 `asyncP`라고 하는 비동기 함수를 호출하면서 그 밑에서 일어나는 모든 일들을 전부 `main` 안에 있는 `try` , `catch`에서 처리하는 방식으로 되어있다. 만약 `asyncP`에서 에러를 처리한 다음에 정상적인 결과를 보내고 싶다면 `asyncP`에서 `await p(1000)`을 `try`, `catch`로 감싸서 에러에 대한 처리를 하고, 정상적으로 코드가 진행돼서 리턴될 수 있게 하면 된다.

<br />

### finally
`try`, `catch`로 처리가 된 후에 마지막에 항상 실행할 무언가를 설정하는 방법이다.
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject(new Error('reason'))
    }, ms);
  });
}

async function asyncP() {
  const ms = await p(1000);
  return 'lightix' + ms;
}

async function main() {
  try {
    const name = await asyncP();
    console.log(name);
  } catch (error) {
    console.log(error);
  } finally {
    console.log('end');
  }
}

main();
```
만약에 `try`로 진횅이 정상적으로 되다가 `console.log('end')`가 될 것이고, 문제가 생기면 `catch`에서 에러가 출력되고 그 다음에 `console.log('end')`가 진행된다.


<br />

### 연속된 Promise 처리와 async await 처리 방법 비교
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

// Promise
p(1000)
  .then(() => p(1000))
  .then(() => p(1000))
  .then(() => {
  console.log('3000 ms 후에 실행된다.');
  });

// async await
async function main() {
  await p(1000);
  await p(1000);
  await p(1000);
  console.log('3000 ms 후에 실행된다.');
}
```
Promise 처리는 연속으로 리턴되서 체이닝처럼 처리를 하게 되고, async await 처리는 한 줄 한 줄이 비동기가 끝나면 진행된다.

<br />

### Promise.all 을 async await로 처리하는 방법
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

async function main() {
  const results = await Promise.all([p(1000), p(2000), p(3000)]);
  console.log(results);
}

main();
```
인자로 넣어준 `p`함수가 전부 실행되면 값(배열)이 `results`로 넘어온다.

<br />

### Promise.race 를 async await로 처리하는 방법
```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

async function main() {
  const result = await Promise.race([p(1000), p(2000), p(3000)]);
  console.log(result);
}

main();
```
인자로 넣어준 `p`함수 중 먼저 실행되는 값이 있다면 바로 `result`로 넘어오게 된다.

<br />

##### 출처
- [패스트캠퍼스 온라인강의](https://www.fastcampus.co.kr/)
- [Poiema Web](https://poiemaweb.com/js-data-type-variable)
- [Velopert](https://learnjs.vlpt.us/async/)