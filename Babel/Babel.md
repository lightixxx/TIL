# Babel
babel은 자바스크립트 컴파일러로, 자바스크립트 코드로 입력하고, 자바스크립트 코드로 출력된다.

최신문법(ES6 이상)으로 개발을 해도 구 브라우저에서 동작할 수 있게 만들어준다.

## 사용법
1. 프로젝트 초기화 및 package.json 생성
```powershall
npm init -y
```

2. Babel 설치
```powershall
npm install --save-dev babel-cli
npm install --save-dev babel-preset-es2015
```

3. 자바스크립트 파일(test.js) 작성
```js
const test = () => {
  console.log('Hello babel')
}
```
