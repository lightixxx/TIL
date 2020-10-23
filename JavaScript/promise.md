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

## resolve & then

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

## reject & catch

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

## finally
fulfilled 되거나 rejected 된 후에 최종적으로 실행할 것이 있다면, `.finally()` 를 설정하고, 함수를 인자로 넣는다.
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
}).finally(() => {
  console.log('end');
})
```

<br />

## promise가 없다면 ?
보통 비동기 작업을 할 때, callback 함수를 인자로 넣어 로직이 끝나면 callback 함수를 호출한다. 이런 경우 함수가 아래로 진행되지 않고, callback 함수 안으로 진행된다.
```jsx
// 일반적인 콜백함수의 진행
function c(callback) {
  setTimeout(() => {
    callback();
  }, 1000)
}

c(() => {
  console.log('1000ms 후에 callback 함수가 실행됩니다.');
});

c(() => {
  c(() => {
    c(() => {
      console.log('3000ms 후에 callback 함수가 실행됩니다.');
    });
  });
});
```
함수가 아래로 진행되는 것이 아니라 callback 함수 안으로 중첩되어 들어가는 것이 callback hell 이다.

`then` 함수에서 다시 프로미스 객체를 리턴하는 방법을 통해 체이닝하면, 비동기 작업을 순차적으로 아래로 표현할 수 있다.
```jsx
function p() {
  return new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve();
    }, 1000);
  });
}

p().then(() => {
  return p(); // 1초 뒤 실행
}).then(() => {
  return p(); // 2초 뒤 실행
}).then(() => {
  return p(); // 3초 뒤 실행
}).then(() => {
  console.log('4000ms 후에 fulfilled 됩니다.')
})
```

### `then`에 함수를 넣는 여러가지 방법
```jsx
function p() {
  return new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve();
    }, 1000);
  });
}

p()
  .then(() => {
    return p(); // 1초 뒤 실행
  })
  .then(() => p()) // 2초 뒤 실행
  .then(p) // 3초 뒤 실행
  .then(() => {
    console.log('4000ms 후에 fulfilled 됩나다.')
  })
```

<br />

## Promise.resolve();
Promise라는 전역 객체 안에 있는 resolve 함수를 실행하면서 promise 객체를 만들어 내는 방법이다. 
```jsx
Promise.resolve(/* value */);
```
value가 프로미스 객체인지 아닌지 알 수 없는 경우, 사용하면 연결된 `then` 메서드를 실행한다.
- value가 프로미스 객체면, resolve 된 then 메서드를 실행한다.
- value가 프로미스 객체가 아니면, value를 인자로 보내면서 `then` 메서드를 실행한다.

<br />

```jsx
Promise.resolve(new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('foo');
  }, 1000);
})).then((data) => {
  console.log('프로미스 객체인 경우, resolve 된 결과를 받아서 then이 실행된다.', data);
})
```
Promise 객체가 resolve된 후에 then이 이어진다.

```jsx
Promise.resolve('bar').then(data => {
  console.log('then 메서드가 없는 경우, fulfilled 된다.', data);
})
```
객체를 넣는 자리에 객체가 아닌 그냥 value를 넣게 되면, resolve 될 것이 없기 때문에 바로 `then` 이 실행된다.

어떤 객체가 Promise 객체인지 데이터 객체인지 모를 때, `Promise.resolve()`로 한 번 실행해서 넘기면 유용하다.

<br />

## Promise.reject();
Promise.reject 를 사용하면, catch로 연결된 rejected 상태로 변경된다.

```jsx
Promise.reject(/* value */);
```
value에 주로 error 객체가 들어온다.

```jsx
Promise.reject(new Error('reason')).then(error => {

}).catch(error => {
  console.log(error);
})
```
reject이기 때문에 then은 넘어가고 바로 catch로 넘어간다.

<br />

## Promise.all([프로미스 객체들])
비동기 작업을 동시에 시작해서 모두 완료되었을 때 처리해 줄 것이 있다면 이 방법을 사용하면 좋다.프로미스 객체 여러개를 생성해서 배열로 만들어 인자로 넣고 `Promise.all` 을 실행하면, 배열의 모든 프로미스 객체들이 fulfilled 되었을 때, `then` 의 함수가 실행된다. `then` 의 함수의 인자로 프로미스 객체들의 resolve 인자값을 배열로 돌려준다. 

```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

Promise.all([p(1000), p(2000), p(3000)]).then((message) => {
  console.log('모두 fulfilled 된 이후에 실행된다.', message);
});
```
위 코드는 3초 후에 콘솔에 '모두 fulfilled 된 이후에 실행된다.' [1000, 2000, 3000] 을 출력된다.

<br />

## Promise.race([프로미스 객체들])
`Promise.all`과 비슷하지만 `all`은 모두 fulfilled 상태가 되었을 때 실행이 되는 반면, `race`는 배열의 모든 프로미스 객체들 중 가장 먼저 fulfilled 된 것으로, `then` 의 함수가 실행된다. 그리고 `then` 의 함수의 인자로 가장 먼저 fulfilled 된 프로미스 객체의 resolve 인자값을 돌려준다.

```jsx
function p(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(ms);
    }, ms);
  });
}

Promise.race([p(1000), p(2000), p(3000)]).then((message) => {
  console.log('가장 빠른 하나가 fulfilled 된 이후에 실행된다.', message);
});
```
위 코드는 1초 후에 콘솔에 '가장 빠른 하나가 fulfilled 된 이후에 실행된다.' 1000 을 출력한다.

<br />

##### 출처
- [poiemaWeb](https://poiemaweb.com/es6-promise)
