# 목록을 작성하는 태그
1. `<ul>`
2. `<ol>`
3. `<dl>`


<br />

## `<ul>` 순서가 없는 목록(Unordered List)
순서가 중요하지 않은 목록이나, 순서가 바뀌어도 의미가 변하지 않는 목록을 작성할 때 사용하는 태그이다.
- 상품순서, 메뉴순서 등
```html
<ul>
  <li>첫 번째 상품</li>
  <li>두 번째 상품</li>
  <li>세 번째 상품</li>
</ul>
```

<br />

## `<ol>` 순서가 있는 목록(Ordered List)
순서가 중요한 목록을 작성할 때 사용하는 태그이다.
- 실시간 검색어, 요리법, 배송과정 등
```html
<ol>
  <li>물을 끓인다</li>
  <li>스프를 넣는다</li>
  <li>면을 넣는다</li>
</ol>
```

### 🚨 `<ul>`과 `<ol>`의 직계자식은 무조건 `<li>`만 가능하다!
다른 태그를 넣으면, 실행은 되지만 웹 표준에 어긋난다.

<br />

## `<dl>` 설명/정의 목록(Description List)
1. 용어를 정의할 때 사용하는 태그이다. (사전에서 단어와 단어의 뜻)
2. key-value로 정보를 제공할 때 사용하는 태그이다. ( {name: 'lightix'} )

### 🚨 `<dl>`의 자식요소로는 `<dt>`, `<dd>`, `<dfn>`, `<div>`가 올 수 있다.
- `<dt>` - 용어 / key (description term)
- `<dfn>` - 의미를 구체적으로 정의내릴 때 (definition)
- `<dd>` - 설명 / value (description data)

<br />

### `<dl>` 사용의 좋은 예와 나쁜 예
```html
<!-- GOOD -->
<dl>
  <dt>
    <dfn> development </dfn>
  </dt>
  <dd> 1. [u] 발달, 성장 </dd> <!-- development에 대한 설명 -->
  <dd> 2. [u,c] (신제품의) 개발; 신개발품 </dd> <!-- development에 대한 설명 -->
</dl>
<dl>
  <dt>라이틱스</dt> <!-- 같은 의미일 때 -->
  <dt>lightixxx</dt> <!-- 같은 의미일 때 -->
  <dd>라이틱스의 블로그입니다.</dd>
</dl>
<dl>
  <dt>라이틱스</dt>
  <dd>라이틱스의 블로그입니다.</dd> <!-- 같은 의미일 때 -->
  <dd>lightixxx의 블로그입니다.</dd> <!-- 같은 의미일 때 -->
</dl>
<dl>
  <div>
    <dt>사과</dt>
    <dd>사과에 대한 설명</dd>
  </div> <!--div로 묶기도 가능 -->
  <div>
    <dt>바나나</dt>
    <dd>바나나에 대한 설명</dd>
  </div> <!--div로 묶기도 가능 -->
</dl>
```

```html
<!-- BAD -->
<dt>
  라이틱스 <!-- dt와 dd는 반드시 dl의 자식요소로 존재해야 한다-->
</dt>
<dl>
  <dt>라이틱스</dt>
  <dd>라이틱스의 블로그입니다.</dd>
  <dt>구글 짱</dt> <!-- 다른 의미인데 따로 설명이 없음 -->
</dl>
<dl>
  <section>
    <dt>사과</dt>
    <dd>사과에 대한 설명</dd>
  </section> <!-- div로만 묶을 수 있음 -->
  <section>
    <dt>바나나</dt>
    <dd>바나나에 대한 설명</dd>
  </section> <!-- div로만 묶을 수 있음 -->
</dl>
```