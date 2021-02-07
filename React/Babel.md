# Babel
babel은 자바스크립트 컴파일러로, 자바스크립트 코드로 입력하고, 자바스크립트 코드로 출력된다. 최신문법(ES6 이상)으로 개발을 해도 구 브라우저에서 동작할 수 있게 만들어준다.

react로 개발을 하다보면, webpack과 더불어 babel은 세트처럼 사용한다.

<br />

## 사용법
### 프로젝트 초기화 및 package.json 생성
```powershall
npm init -y
```

<br />

### babel/core 랑 babel/cli 설치
```powershall
npm i -D @babel/core @babel/cli

<!-- 안되면 -->
npx babel

<!-- 전역 설치 -->
npm i -g @babel/core @babel/cli

```
- babel/core : 코드를 구 브라우저에서 돌아가게 변환해주는 역할
- babel/cli : Command Line Interface 명령어를 사용할 수 있게 해주는 역할

<br />

### babel 사용 옵션
babel을 사용하기 위해선 옵션을 설정해야 한다. (src 폴더 안에 있는 모든 directory를 다른 폴더로 변환하겠다.)
```powershall
<!-- src 안에 있는 모든 directory를 dist 폴더로 변환해서 이동하겠다. -->
babel src -d dist
```

<br />

### 예제 파일 작성
```js
// src/Person.js
class Person {
  constructor(name) {
    this.name = name
  }
  eat(food) {
    console.log(`${this.name}이 ${food}를 먹는다`)
  }
}

new Person("lightix").eat();
```

class, template literal(``)는 최신 문법이기 때문에 옛날 브라우저에서 사용할 수 없다. 

다시 `babel src -d dist`을 하게 되면, dist 디렉토리 안에 Person.js가 구버전 브라우저에서 돌아갈 수 있는 형태로 변환되어 저장될 것 같지만 그냥 복사되어 저장된다. 이유는 바벨을 어떤 브라우저에 맞춰서 컴파일하게 할 지 세팅을 안해주었기 때문이다.

<br />

### babel/preset-env 설치
```powershall
npm i -D @babel/preset-env
```
preset environment 바벨을 이용할 때 어떤 환경을 조절할 수 있게 정리되어 있는 모음집(?) 같은 것이라고 생각하면 된다.

<br />

### 루트에 .babelrc 파일 생성
```json
{
  "presets": ["@babel/preset-env"]
}
```
.babelrc는 json 형태로 작성하면 된다. 바벨이 실행될 때, 설정 값에 맞춰서 실행되도록 세팅하는 파일이라고 생각하면 된다. 

babel을 실행할 때, .babelrc 파일이 없다면 기본값으로 실행이 되는데, 프로젝트 루트(package.json과 같은 위치)에 .babelrc 파일이 있다면 babel의 설정파일로 알아보고 그 파일의 내용으로 실행하게 된다.

<br />

### 변환된 js파일 연결하기
```html
<!-- public/index.html -->
<script src="../dist/index.js"></script>
```
src안에 있는 파일은 개발할 때 사용하는 파일이고, 실제로 배포를 나갈 때는 babel을 통해 변환된 파일(dist폴더 안)을 바라보게 해야한다.

> dist: distribution의 약자로 배포용 코드를 담아두는 디렉터리를 의미한다. 자바스크립트로 라이브러리를 만들 때, 관례적으로 사용하는 표현이다.

<br />

### watch 옵션 주기
```powershall
babel src -d dist --watch
```
watch 옵션으로 babel을 실행하게 되면, babel이 종료되지 않고 소스 코드가 변경될 때 마다 알아서 컴파일을 진행한다.

예를 들어 바벨만 이용해서는 

<br />

바벨은 그 코드를 옛날 브라우저에서 돌아가게끔 코드를 변환할 뿐이고, 그 변환된 코드가 브라우저에서 실행되는 함수인지 아닌지는 바벨이 알지 못한다.

예를 들어 브라우저에서 모듈을 가져오기 위해 `import Person from './Person'`을 바벨을 통해 컴파일하면 require 함수로 변환이 되는데, require 함수는 브라우저에서 알지 못한다. 바벨을 통해서 모듈을 가져오거나, 내보내거나 하는 코드는 이용할 수 없다. 따라서 모듈을 번들링하기 위해서는 webpack을 함께 이용해야 한다.