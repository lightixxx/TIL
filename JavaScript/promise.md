# promise
ES6부터 추가된 표준 내장 객체이다. 전통적인 콜백 패턴이 가진 단점(콜백지옥)을 보완하며 비동기 처리 시점을 명확하게 표현할 수 있다는 장점이 있다.

- promise 생성자를 통해서 인스턴스화한다.
- 생성자의 인자로는 executor 라는 함수를 이용한다.

```jsx
// Promise 객체의 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업을 수행한다.

  if(/* 비동기 작업 수행 성공 */) {
    resolve('result');
  } else {
    /* 비동기 작업 수행 실패 */
    reject('failure reason');
  }
});
```
Promise는 비동기 처리가 성공했는지 실패했는지 등의 상태 정보를 갖는다.

Promise 생성자 함수가 인자로 전달받은 콜백 함수는 내부에서 비동기 처리 작업을 수행한다. 이때 비동기 처리가 성공하면 콜백 함수의 인자로 전달받은 resolve 함수를 호출한다. 이때 프로미스는 'fulfilled' 상태가 된다. 비동기 처리가 실패하면 reject 함수를 호출한다. 이때 프로미스는 'rejected' 상태가 된다.

## executor
executor 함수는 resolve 와 reject를 인자로 갖는다. 


##### 출처
- [poiemaWeb](https://poiemaweb.com/es6-class)
- fastcampus 온라인강의