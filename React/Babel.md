# Babel
babel은 자바스크립트 컴파일러로, 자바스크립트 코드로 입력하고, 자바스크립트 코드로 출력된다. 최신문법(ES6 이상)으로 개발을 해도 구 브라우저에서 동작할 수 있게 만들어준다.

react로 개발을 하다보면, webpack과 더불어 babel은 세트처럼 사용한다.

<br />

## 사용법
1. 프로젝트 초기화 및 package.json 생성
```powershall
npm init -y
```

2. babel/core 랑 babel/cli 설치
```powershall
npm i -D @babel/core @babel/cli

<!-- 전역 설치 -->
npm i -g @babel/core @babel/cli
```
- babel/core : 코드를 구 브라우저에서 돌아가게 변환해주는 역할
- babel/cli : Command Line Interface 명령어를 사용할 수 있게 해주는 역할


3. babel 사용 옵션
babel을 사용하기 위해선 옵션을 설정해야 한다. (src 폴더 안에 있는 모든 directory를 다른 폴더로 변환하겠다.)
```powershall
<!-- src 안에 있는 모든 directory를 dist 폴더로 변환해서 이동하겠다. -->
babel src -d dist
```

4. 예제 파일 작성
```js
// src/sum.js
const sum = (a, b) => {
  return a + b
}
```
다시 `babel src -d dist`을 하게 되면, dist 디렉토리 안에 sum.js가 구버전 브라우저에서 돌아갈 수 있는 형태로 변환되어 저장된다.

