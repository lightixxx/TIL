# Web-app

## 웹의 기본 구성요소

보통 웹 어플리케이션을 만드는데 필요한 구성 요소는 HTML, CSS, JavaScript로 3가지가 있다. 하지만 무엇을 만드는지에 따라 반드시 있어야 되고 없어도 되는 것들이 달라진다. 단순히 웹페이지만 만든다면 사실 HTML만 있어도 만들 수 있다. 모양을 꾸미고 싶다면 당연히 CSS가 있어야한다. HTML과 CSS로만 만들어진 웹페이지들은 정적이고 무언가 변화없이 사용자에게 똑같은 형태의 정보만을 제공해 주는 목적으로 만들어진 것이기 때문에 앱이라고 부르지 않고 보통 페이지 혹은 문서라고 부른다.

어플리케이션으로써 상태라는 것을 갖고 있고, 사용자와 상호적으로 주고 받을 수 있는 다양한 기능들을 제공해 주는 것들을 앱이라고 부른다. 따라서 앱이 되기 위해서는 반드시 JavaScript가 필요하다. 웹앱을 개발하기 위해선 HTML, CSS, JavaScript 이 3개는 모두 다 같은 비중으로 필수불가결한 요소라고 할 수 있다.

실제로 어떤 관점을 갖고 있는지에 따라 구성요소를 다양하게 설명할 수 있다.

<br />

## 실행 관점의 구성요소

가장 일반적으로 웹앱이 실행된다고 하는 관점에서 구성요소를 설명하자면, 웹앱이 실행된다는 것은 사용자가 브라우저를 실행시킨 다음에 주소창에 특별한 웹사이트 주소를 입력하는 것이다. 그 웹사이트에 접속을 하면 HTML, CSS, JavaScript라고 하는 실제 파일들이 물리적으로 사용자의 브라우저에 전송되고, 브라우저가 그 파일들을 해석해서 실행시키면 웹앱이 동작하는 형태가 만들어진다.

알다시피 HTML은 UI를 기본적으로 만들고, CSS는 그 UI의 비주얼적인 요소를, JavaScript는 동적이고 프로그래밍적인 부분을 담당하게 된다. 위에서 말한 것과의 차이점은 구성 요소로써 굉장히 중요한 브라우저라고 하는 것이 추가됐다는 것이다. 즉, 웹앱을 실행시키는 역할을 하는 것이 브라우저이다. 다른 말로 표현하면 실행되는 시간, 실행 시간이라고해서 보통 런타임이라는 표현을 사용한다. 보통 브라우저를 런타임 환경을 제공하는 환경이라고 얘기한다. 다시말해 웹앱에 런타임 환경을 제공하는 것이 브라우저가 될 수 있다.

예전에는 브라우저만이 JavaScript를 실행시키는 런타임 환경을 제공하는 유일한 환경이었지만, 십여년 전부터 Nodejs라고 하는 애플리케이션이 나오면서 이젠 브라우저가 아니어도 JavaScript를 실행시킬 수 있는 환경이 다수 만들어졌다.

<br />

## CSR & SSR

관점을 달리해보면, UI를 만드는 것이 HTML의 역할이고, JavaScript를 이용해 HTML을 조작할 수 있기 때문에 JavaScript를 이용해서도 UI를 제공할 수 있다. 결론적으로 어떤 식으로든 UI를 만들기 위해선 최종적으로 HTML 형태가 만들어져 있어야 되기 때문에 HTML을 어디에서 만드는 가가 굉장히 중요하다. 'HTML을 언제 만드는가'라고 하면 브라우저가 HTML을 로딩할 때는 웹 서버라고 하는 소프트웨어가 HTML 파일을 브라우저한테 전송해준다. 그렇다고 하는 것은 전송하기 전에는 웹서버 안에 HTML 파일이 존재하는 것이다. 그 후에 브라우저 안에 HTML이 전송된 후에 HTML을 해석해서 브라우저가 화면에 UI를 그리고 난 후, JavaScript가 실행이 된다. JavaScript가 HTML을 조작할 수 있다는 것은 브라우저가 웹앱을 실행시킨 다음에도 JavaScript에 의해서 UI가 조작되는 경우도 있다고 이해하면 된다.

이 관점에서 실제로 브라우저에 최초로 전송된 HTML에는 거의 내용이 없고, JavaScript가 실행되면서 필요한 UI를 그때그때마다 JavaScript가 생성해 내는 방식을 클라이언트 사이드 렌더링(CSR)이라고 부른다.

또 하나의 방식은 JavaScript의 실행 결과로 HTML이 만들어지는 것이 아니라, 웹 서버에서 HTML파일을 만들어 브라우저로 전송되는 방법이 있으며 이것을 서버 사이드 렌더링(SSR)이라고 부른다.

중요한 것은 어떤 웹앱이든 CSR로 개발할 수도 있고, SSR로 개발을 할 수도 있다. 단지 그 앱의 성격에 따라서 어떤 방식이 더 효과적인지가 달라진다. 반대로 앱의 성격에 맞지 않는 렌더링 방식을 선택했을 때는 비효율이 발생할 수도 있는 것이다. 따라서 개발자의 역할이 중요하다.

실제 물리적인 단위들인 HTML, CSS, JavaScript와 같은 파일들의 구성에 대해 설명했지만, 그 외에도 실제 프로그래밍적인 관점에서의 구성 요소들도 다양하게 있다. HTML로 UI를 만들고 JavaScript를 통해 조작을 하는 것은 똑같지만, 실제로 그 안에 다양한 부가 시스템들이 존재한다.

<br />

## 그래픽 시스템

웹앱 자체는 기본적으로 그래픽 시스템을 HTML과 CSS를 가지고 그래픽을 표현할 수 있다. 사각형 박스, 동그라미, 그라데이션, 섀도우 등 이런 식의 그래픽 요소들을 HTML과 CSS를 갖고 만들 수 있다. 그 이상의 적극적인 그래픽 시스템들이 필요한 경우도 있다. 차트를 만들거나, 유려한 애니메이션을 표현한다거나, 혹은 3D를 표현한다거나 했을 때 HTML과 CSS만 갖고는 한계가 있다.

따라서 JavaScript를 갖고 3D 혹은 2D 그래픽들을 표현할 수 있게 제공해주는 캔버스라고 하는 태그가 있고, 그 태그는 일종의 그래픽 시스템을 표현하기 위한 도화지이다. 캔버스 태그는 2D나 3D 그래픽을 표현하기 위한 영역만을 제공하고, 실질적으로 그래픽을 작업하는건 JavaScript 코드로 이루어진다. 그래서 JavaScript 코드로 그래픽을 다룰 수 있는 다양한 도구들을 제공한다. 이런 도구들을 API라고 보통 얘기하는데, JavaScript로 다룰 수 있는 형태로 제공된다.

웹 프론트엔드 개발자들이 HTML과 CSS만을 다루는 게 아니라 필요에 의해서 2D나 3D 그래픽을 할 수도 있다. 물론 그 자체로 굉장히 다양한 추가적인 지식들을 요구하지만, 간단한 차트라든가 간단한 그래픽 시스템들은 프론트엔드 개발자한테 필수불가결한 지식 중에 하나이다.

그 외에도 웹앱을 이루는 다양한 구성 요소가 있다. 예를 들어 미디어 파일을 다루거나 혹은 웹 워커, 웹 어셈블리라고 하는 스펙들도 있다.

<br />

#### 출처

- [패스트캠퍼스 JavaScript & TypeScript Essential](https://fastcampus.co.kr/dev_academy_kmt1)
