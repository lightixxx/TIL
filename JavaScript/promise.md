# promise
ES6부터 추가된 표준 내장 객체이다. 전통적인 콜백 패턴이 가진 단점(콜백지옥)을 보완하며 비동기 처리 시점을 명확하게 표현할 수 있다는 장점이 있다.

- promise 생성자를 통해서 인스턴스화한다.
- 생성자의 인자로는 executor 라는 함수를 이용한다.

```jsx
new Promise((resolve, reject) => {}); // pending
```
생성자를 통해서 프로미스 객체를 만드는 순간 pending(대기) 상태가 된다.

```jsx
// Promise 객체의 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업을 수행한다.

  if(/* 비동기 작업 수행 성공 */) {
    resolve('result'); // fulfilled (이행)
  } else {
    /* 비동기 작업 수행 실패 */
    reject('failure reason'); // rejected (거부)
  }
});
```
Promise는 비동기 처리가 성공했는지 실패했는지 등의 상태 정보를 갖는다.

Promise 생성자 함수가 인자로 전달받은 콜백 함수는 내부에서 비동기 처리 작업을 수행한다. 이때 비동기 처리가 성공하면 콜백 함수의 인자로 전달받은 resolve 함수를 호출한다. 이때 프로미스는 'fulfilled' 상태가 된다. 비동기 처리가 실패하면 reject 함수를 호출한다. 이때 프로미스는 'rejected' 상태가 된다.

<br />

## executor
executor 함수는 resolve 와 reject를 인자로 갖는다. 

<br />

### resolve & then

```jsx
// p 라는 프로미스 객체는 1000ms 후에 fulfilled 된다.
const p = new Promise((resolve, reject) => {
  setTimeout(() =>  {
    resolve(); // fulfilled
  }, 1000);
});
```

```jsx
// p 라는 프로미스 객체는 1000ms 후에 fulfilled 된다.
const p = new Promise((resolve, reject) => {
  setTimeout(() =>  {
    resolve();
  }, 1000);
});

// fulfilled 되는 시점(1초 후)에 p.then 안에 설정한 callback 함수가 실행된다.
p.then(() => {
  // callback function
});
```

보통 실무에서는 Promise 객체를 바로 만들어서 사용하는 것 보다는 실제로 사용하는 곳에서 생성해서 `then`과 엮어주는 방식으로 많이 작업한다. 

```jsx
function p() {
  return new Promise((resolve, reject) => {
    setTimeout(() =>  {
      resolve();
    }, 1000);
  });
}

p().then(() => {
  console.log('1000ms 후에 fulfilled 됩니다.')
});
```
`then`을 설정하는 시점을 정확히하고, 함수의 실행과 동시에 프로미스 객체를 만들면서 pending이 시작하도록 하기 위해 promise 객체를 생성하면서 리턴하는 함수 `p`를 만들어 함수 `p` 실행과 동시에 then을 설정한다.

<br />

### reject & catch

```jsx
// promise 객체가 rejected 되는 시점에 `p.catch` 안에 설정한 callback 함수가 실행된다.
function p() {
  return new Promise((resolve, reject) => {
    setTimeout(() =>  {
      reject(); // rejected
    }, 1000);
  });
}

p().then(() => {
  console.log('1000ms 후에 fulfilled 됩니다.');
}).catch(() => {
  console.log('1000ms 후에 rejected 됩니다.');
});
```

<br />

executor의 resolve 함수를 실핼할 때 인자를 넣어서 실행하게 되면, `then`의 callback 함수의 인자로 받을 수 있다.

```jsx
function p() {
  return new Promise((resolve, reject) => {
    setTimeout(() =>  {
      resolve('fulfilled'); // 메세지나 객체 등 다양한 정보를 담아서 보낼 수 있다.
    }, 1000);
  });
}

p().then((message) => {
  console.log(`1000ms 후에 ${message} 됩니다.`);
}).catch(() => {
  console.log('1000ms 후에 rejected 됩니다.');
});
```
보통 비동기 작업이라고 하는 것은 어떤 원격에 있는 데이터를 가져올 때 많이 사용한다. 원격으로 요청하고 정상적으로 수행이 됐을 때, 받아온 데이터를 `then`으로 넘겨받아서 활용하는 데 많이 사용하게 된다.

<br />

마찬가지로 executor의 reject 함수를 실핼할 때 인자를 넣어서 실행하게 되면, `catch`의 callback 함수의 인자로 받을 수 있다.
```jsx
function p() {
  return new Promise((resolve, reject) => {
    setTimeout(() =>  {
      reject('error');
    }, 1000);
  });
}

p().then((message) => {
  console.log(`1000ms 후에 ${message} 됩니다.`);
}).catch((reason) => {
  console.log(`1000ms 후에 ${reason}때문에 rejected 됩니다.`);
});
```
하지만 보통은 자바스크립트에서 사용하는 error 객체를 만들어서 넘기는 것이 일반적이다.

```jsx
function p() {
  return new Promise((resolve, reject) => {
    setTimeout(() =>  {
      reject(new Error('bad'));
    }, 1000);
  });
}

p().then((message) => {
  console.log(`1000ms 후에 ${message} 됩니다.`);
}).catch((error) => {
  console.log('1000ms 후에 rejected 됩니다.', error);
});
```


<br />

##### 출처
- [poiemaWeb](https://poiemaweb.com/es6-promise)
