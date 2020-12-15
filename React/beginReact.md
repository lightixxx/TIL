# React
화면을 만들기 위한 기능들을 모아놓은 자바스크립트 라이브러리이다.

<br />

## 장점
1. 화면을 빠르게 업데이트한다.
     - Virtual DOM
2. 렌더링 속도가 빠르다.
3. 리액트는 모든 페이지가 컴포넌트로 구성되어 있고, 하나의 컴포넌트는 또 다른 컴포넌트의 조합으로 구성될 수 있다.
      - 재사용성이 높아서 개발속도가 빨라진다.
4. 계속해서 개발이 되고있는 라이브러리이다.
5. 활발한 지식공유가 이루어지고 있다.
6. React Native로 모바일앱도 개발 가능하다.

<br />

## 단점
1. 새로운 개념과 버전에 대한 꾸준한 학습이 필요하다.

<br />

[counter](https://github.com/lightixxx/reactBasic/tree/main/counter) 와 [modal](https://github.com/lightixxx/reactBasic/tree/main/modal) 예시에선 DOM을 선택해서 원하는 이벤트가 발생할 때 속성을 바꾸어야 한다. 사용자와의 인터렉션에 따라 동적으로 UI를 그려야한다면 규칙이 복잡해지고, 관리 및 유지보수도 힘들어 질 것이다.

리액트는 Virtual DOM을 사용해 메모리에 가상으로 존재하는 DOM을 사용해서 상태가 업데이트되면, 업데이트가 필요한 곳의 UI만 Virtual DOM을 통해 렌더링한다. 그리고 나서 실제 브라우저에 보여지고 있는 DOM과 비교한 후, 차이가 있는 곳을 감지해서 이를 실제 DOM에 패치시킨다.

<br />

## 작업환경 준비
- Node.js: 자바스크립트 런타임인 Node.js는 Webpack과 Babel 같은 도구를 사용하기 위해 설치해야 한다.
- Yarn: npm과 마찬가지로 패키지 매니저 도구이다. 프로젝트에서 사용되는 라이브러리를 설치하고, 해당 라이브러리의 버전 관리를 할 때 사용한다.

<br />

## create-react-app

1. node를 설치한다.
2. 터미널에 `npx create-react-app appName`을 입력해서 사용할 준비를 한다.
3. 설치가 완료되면 `cd appName`로 디렉토리를 옮기고, `npm start`를 하면 3000번 포트에서 앱이 실행된다.
4. production build를 만들기 위해 `npm run build`를 입력한다.
5. `sudo npm install -g serve`로 serve를 설치한다.

<br />

### 자동으로 생성되는 파일
1. node_modules - 설치한 라이브러리를 모은 폴더
2. public - static 파일을 모아놓는 폴더 (image, favicon 등)
3. src - 소스코드 보관함으로 실질적인 코딩을 하는 폴더
4. package.json - 설치한 라이브러리 명과 버전을 모아놓는 파일


<br />
<br />
<br />

##### 출처
- [벨로퍼트 블로그](https://react.vlpt.us/basic/01-concept.html)
- [소플](https://edu.goorm.io/learn/lecture/12976/%EC%B2%98%EC%9D%8C-%EB%A7%8C%EB%82%9C-react-%EB%A6%AC%EC%95%A1%ED%8A%B8/info)
- [코딩애플](https://youtu.be/nahwuaXmgt8)