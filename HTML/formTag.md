# form 태그와 관련된 태그

## `<input />`
웹에서 사용자의 데이터를 받을 수 있는 대화형 컨트롤을 생성한다. 

🚨 필수 attribute로 type을 작성해야 한다.
```html
<form action=" " method=" ">

  <!-- 한 줄 정도의 간단한 텍스트를 입력하는 경우 -->
  <input type="text" />
  
  <!-- 숫자를 입력하는 경우 -->
  <input type="number" /> 
  
  <!-- 비밀번호를 입력하는 경우 -->
  <input type="password" /> 
  
  <!-- 이메일을 입력하는 경우 -->
  <input type="email" />
  
  <!-- 전화번호를 입력하는 경우 -->
  <input type="tel" /> 
  
  <!-- 라디오 버튼을 만드는 경우 -->
  <input type="radio" /> 
  
  <!-- 기본 버튼을 만드는 경우 -->
  <input type="button" /> 
  
  <!-- 제출하는 버튼을 만드는 경우 -->
  <input type="submit" /> 
  
  <!-- 파일을 업로드하는 경우 -->
  <input type="file" /> 
  
  <!-- 그 외 -->
  <!-- checkbox, color, reset, search, url 등 -->
  
<form>
```

### type 외에 추가할 수 있는 attribute
- placeholder="기본 안내 문구" : 기본적으로 안내 문구를 제공할 수 있다.
- maxlength="15" - input에 입력 가능한 최대 문자 수를 설정할 수 있다.
- minlength="5" - input에 입력 가능한 최소 문자 수를 설정할 수 있다.
- required - 필수로 입력해야 하는 정보일 때 사용한다.
- disable - 특정 input 값을 사용하지 못하게 막아둘 때 사용한다.
- value="sample text" - 미리 입력되어 있는 상태로 시작하고 싶을 떄 사용한다.
- max="99" - `<input type="number" />`에서 숫자의 최대값을 지정할 수 있다.
- max="99" - `<input type="number" />`에서 숫자의 최대값을 지정할 수 있다.
- accept=".png, .jpg" - `<input type="file" />`에서 파일의 확장자를 제한할 때 사용한다.

<br />

## `<label>`
폼 양식에 이름을 붙이는 태그이다.

🚨 필수 attribute로 input의 id 값을 for에 작성해야한다.
```html
<label for="inputId"> 라벨 </label>
<input id="inputId" type="text" />
```
label을 누르면 input에 focus가 되기 때문에 사용성이 개선된다.

<br />

## `<radio>`
`<input type="radio" />`는 여러가지 항목 중 단 한 개만 선택할 수 있는 버튼을 생성할 때 사용한다. 

🚨 필수 attribute로 `name`과 `value`를 작성해야 한다. 
- `name`은 같은 값을 적게되면 radio 그룹으로 묶어줄 수 있기 때문에 같은 값이 작성된 input은 단 한개만 선택할 수 있다.
- `value`는 다른 값을 적어서, submit했을 때 서버에서 구분하기 위해 작성해야 한다.
```html
<form action=" " method="GET"> 
  
  <input type="radio" name="user-sex" id="male" />
  <label for="male"> 남자 </label>
  
  <input type="radio" name="user-sex" id="male" />
  <label for="female"> 여자 </label>
  
  <button type="submit"> submit </button>
  
</form>
```

<br />

## `<checkbox>`
`<input type="checkbox" />`는 여러가지 항목을 선택할 수 있는 버튼을 생성할 때 사용한다.

🚨 필수 attribute로 `name`과 `value`를 작성해야 한다. 
- `name`은 같은 값을 적어서 checkbox 그룹을 묶어준다.
- `value`는 다른 값을 적어서, submit했을 때 서버에서 구분하기 위해 작성해야 한다.
```html
<h1> 취미 </h1>

<form action=" " method="POST">

  <input type="checkbox" name="hobby" value="design" id="design" />
  <label for="design"> 디자인 </label>
  
  <input type="checkbox" name="hobby" value="photograph" id="photograph" />
  <label for="photograph"> 사진촬영 </label>
  
  <input type="checkbox" name="hobby" value="video-editing" id="video-editing" />
  <label for="video-editing"> 영상편집 </label>
  
  <button type="submit"> submit </button>
  
</form>
```

<br />

## `<select>` 와 `<option>`
옵션으로 드롭 다운 목록을 작성하는 태그이다.
```html
<form action="" method="GET">

  <label for="hobby">취미</label>
  
  <select name="hobby" id="hobby">
    <option value="design"> design </option>
    <option value="photograph"> photograph </option>
    <option value="videoEditing"> videoEditing </option>
  </select>
  
  <input type="submit" />
</form>
```

### 추가할 수 있는 attribute
- multiple : 여러가지 옵션을 선택한다.
- size : 한 번에 볼 수 있는 행의 개수를 지정한다.
- disabled : 선택 메뉴를 비활성화한다.

<br />

## `<textarea>`
여러 줄의 텍스트를 입력받을 때 사용하는 태그이다.
```html
<label for="field"> 자기소개 </label>
<textarea id="field" placeholder="자기소개를 입력하세요"></textarea>
```
### 추가할 수 있는 attribute
- rows="30" : 양식의 줄 수를 지정한다.(CSS로 조절도 가능)
- maxlength="500" : 입력 가능한 최대 문자 수를 지정한다.
- autofocus : 페이지가 로드될 때 자동으로 포커스가 된다.
- placeholder="자기소개" : 기본 안내 문구를 제공한다.
- disabled : 양식을 비활성화한다.

<br />

## `<button>`
선택 가능한 버튼을 만들 때 사용하는 태그이다.
```html
<!-- 자바스크립트를 이용한 기능 구현에 주로 사용 -->
<button type="button"> 버튼 </button>

<!-- 폼의 전송 전송 기능 -->
<button type="submit"> 확인 </button>

<!-- 폼 작성 내용 초기화 기능 -->
<button type="reset"> 다시 쓰기 </button>
```

### `<button type="button">` VS `<a href="#">` VS `<input type="button">`
1. `<input type="button">` 보다 스타일링하기 자유롭고, 태그 안에 다른 태그 삽입도 가능하다.
2. `<a>`태그는 문서 간 연결이 주된 목적이기 때문에 링크에만 사용하는 것이 좋고, 기능 구현은 button으로 하는 것이 시멘틱한 마크업이다.