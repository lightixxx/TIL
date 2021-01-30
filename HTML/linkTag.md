# 다른 URL로 연결해주는 링크 태그

### anchor
다른 페이지, 같은 페이지 내 이동, 이메일 주소, 전화번호 등 다른 URL로 연결해주는 `<a>`태그
```html
<a href="#"> #페이지로 이동 </a>
```
href란, **H**ypertext + **ref**erence 로, HTML 문서 혹은 웹페이지의 주소 값을 뜻한다.

<br />

### href 주소값 표기 방법
```html
<!-- 1. 웹페이지 url -->
<a href="https://github.com/lightixxx"> lightixxx 블로그로 이동 </a>

<!-- 2. 페이지 내 이동 -->
<a href="#hello"> 페이지 내 hello라는 섹션으로 이동 </a>

<!-- 3. 메일주소로 이동 -->
<a href="mailto:lightixxx@gmail.com"> lightixxx에게 메일쓰기 </a>

<!-- 4. 전화걸기 -->
<a href="tel:01012345678"> OOO에게 전화걸기 </a>
```

<br />

### target 속성
새 창 또는 새 탭에서 링크열기를 지정할 수 있는 속성이다.
```html
<!-- 1. 연결 문서를 클릭한 창에서 열기 (default) -->
<a href="https://github.com/lightixxx" target="_self"> 라이틱스 블로그 </a> 

<!-- 2. 새 탭으로 이동 --> 
<a href="https://github.com/lightixxx" target="_blank"> 라이틱스 블로그 </a> 

<!-- 3. 부모 창에서 열기 (없다면 _self) --> 
<a href="https://github.com/lightixxx" target="_parent"> 라이틱스 블로그 </a> 

<!-- 4. 가장 상위 창에서 열기 (없다면 _self) --> 
<a href="https://github.com/lightixxx" target="_top"> 라이틱스 블로그 </a>
```

<br />

### title 속성
마우스 호버 시 링크를 미리 알려주는 툴팁을 제공해주는 속성이다.
```html
<a href="https://github.com/lightixxx" title="라이틱스 블로그로 이동합니다.">라이틱스</a>
```
