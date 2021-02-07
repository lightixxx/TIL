# webpack
babel만으로는 모듈을 가져오거나 내보낼 수 없기 때문에 webpack을 통해 모듈을 번들링 한다.

<br />

## 사용법

### 프로젝트 초기화 및 package.json 생성
```powershall
npm init -y
```

<br />

### webpack, webpack-cli 설치
```powershall
npm i -D webpack webpack-cli
<!-- or -->
npx webpack
```
> 터미널에 `webpack`을 입력해서 실행한다. 안될 경우엔 터미널 껐다 켜면 된다.
dist 폴더에 main.js 파일이 생성됐다면, 성공!

<br />

### webpack 옵션 추가
```json
// (package.json)
{
  ...,
  "scripts": {
    "start": "webpack --mode=development",
    ...
  }
}
```
- "start": "webpack --mode=production" : 실제 운영에 배포나갔을 때 사용 (용량 최소, uglify)
- "start": "webpack --mode=development" : 개발할 때 사용 (보기 편함)

<br />

### 예제파일 작성
```js
// Person.js
class Person {
  constructor(name) {
    this.name = name
  }

  eat(food) {
    console.log(`${this.name}이 ${food}를 먹는다`)
  }
}

export default Person;
```

```js
// index.js
import Person from './Person.js'

new Person("lightix").eat("kimchi");
```

```html
<!-- index.html -->
<script src="../dist/main.js"></script>
```

<br />

### webpack.config.js 생성
.babelrc 파일을 babel이 설정파일로 알듯, webpack.config.js 파일이 루트에 있으면 webpack이 해당 파일을 설정파일로 인식한다.

```js
module.exports = {
  mode: "development"
}
```

mode는 package.json에서 설정한 `"start": "webpack --mode=development"`를 사용하지 않고, webpack.config.js에서 따로 설정할 수 있도록 한다. 마찬가지로 `mode: "production"`도 사용할 수 있다.

<br />

```js
module.exports = {
  // mode: "development",
  module: {
    rules: [{
      test: /\.js/,
      exclude: /node_modules/,
      loader: "babel-loader"
    }]
  }
}
```
- `rules`는 webpack에 사용할 rule을 설정한다.
- `test: /\.js/` 는 확장자가 .js인 모든 것들 중에서,
- `excludes: /node_modules/` node_modules에 있는 js파일 빼고 나머지 js파일을,
- `loader: "babel-loader"` babel-loader를 통해서 돌리겠다는 뜻이다.

> error가 난다면 babel-loader를 설치안했기 때문!
> 
> `npm i -D babel-loader`