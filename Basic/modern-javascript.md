# 모던 Javascript와 개발 환경

<br />

## 급변한 프론트엔드 개발 환경

ES2015 버전부터 보통 현대적인 "새로운 JavaScript 버전이겠구나"라고 생각할 수 있고 통상적으로 그렇게 생각을 하지만, 사실상 정답은 없다.

ES2015 버전부터 프론트엔드 개발환경이 급격하게 달라진 것은 아니다. 역사적으로는 ES2015 버전이 나오기 전부터 프론트엔드의 개발 환경은 급변했다. 대표적인 이유는 nodejs 때문에 그렇다. nodejs와 npm으로 이루어지는 생태계 변화, 그리고 제공되는 툴, 툴을 이용한 환경의 변화들 때문에 프론트엔드 개발 환경은 급변했다.

물론 급변하는 과정에서 여러 제안들이 등장했고, 그 제안들이 실제로 표준에 합류하면서 지금의 개발 환경을 만들었다고 할 수 있다. 그런데 이 과정들이 대략 10년 정도에 걸쳐서 이루어졌는데, 엄청난 변화들이 그 안에 포함되어 있다.

핵심적으로 '어떤 부분들이 그 변화를 일으키는데 주된 요소로 작용했는가' 라고 하는 측면들을 모르면, 막연히 프론트엔드 개발환경은 너무 복잡하고 배워야 할 게 너무 많고, 왜 이렇게 복잡하게 되어 있는지 스트레스를 받게 되는 상황까지 올 수 있다. 모르고 스트레스를 받는 것 보다는 '왜 이렇게 되어야만 하는지'에 대한 부분들을 이해하면 복잡한 프로젝트 세팅과 환경 설정과 같은 부분에 스트레스를 덜 받을 수 있다.

프론트엔드 개발환경이 복잡해진 이유는 굉장히 여러 가지가 있다. 그 원인을 모두 알 필요는 없고, 핵심적인 원인 한 가지만 알면 된다. 그것은 바로 **웹앱의 규모가 굉장히 커지고 복잡해졌다는 것**이다. 웹애플리케이션의 규모라고 하면 보통 생각하는 그 상상 이상보다도 엄청 클 수 있다.

소프트웨어 하나를 만든다고 하면 규모가 큰 소프트웨어 하나의 코드는 수십만 라인에서 수백만 라인, 혹은 그 이상이 될 수도 있다. 코드의 규모도 그렇지만 그 코드가 하나의 파일에 다 들어가 있을 수 없기 때문에 수백, 수천 개의 파일이 단 하나의 애플리케이션을 위한 파일이 된다.

JavaScript 역사와 관련해서 아주 초기에 브라우저 안에서 HTML을 조작하기 위한 정도의 가벼운 역할로 시작된 언어가 JavaScript 였다. JavaScript 언어는 아주 간단한 일을 하기 위해서 만들어진 프로그래밍 언어였다. 언어의 디자인 자체가 이렇다 보니 실제로 수만 개의 소스 코드를 갖고 하나의 애플리케이션을 만들기 위해서 필요한 여러 가지 기능들이 하나도 준비가 되어 있지 않았다.

<br />

#### 출처

- [패스트캠퍼스 JavaScript & TypeScript Essential](https://fastcampus.co.kr/dev_academy_kmt1)