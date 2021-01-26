# axios
axios는 http 프로토콜을 이용해서 데이터를 요청하거나 받아올 수 있는 라이브러리 이다. 마치 fetch 위에있는 작은 layer 같은 것.

<br />

## Install
```powershell
npm install axios
```

<br />

## axios.post(주소, 바디)
axios는 모든 메서드들이 프로미스 형태로 지원된다.
```jsx
// Login Promise
axios.post('http://api.lightix.com/vl/me', {
  email,
  password,
}).then(res => {});

const res = await axios.post('http://api.lightix.com/vl/me', {
  email,
  password,
});
```
프로미스이기 때문에 `.then`을 통해 서버로부터 정상적으로 데이터를 가져오면 resolve돼서 res로 정보가 넘어오게 된다. 
