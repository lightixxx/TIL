# Bootstrap
grid system을 css로 쉽게 구현할 수 있게 도와주는 프레임워크이다. 심지어 반응형까지!

## Grid System 사용하기

<br />

### 0. bootstrap CDN 불러오기
```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
```
### 1. container 만들기
```html
<div class="container"></div>
```
### 2. container 자식요소로 row 만들기
```html
<div class="container">
  <div class="row"></div>
</div>
```
부트스트랩은 12컬럼으로 구성되어 있다.

### 3. row 안에 col-n 만들기
```html
<div class="container">
  <div class="row">
    <div class="col-3"></div>
  </div>
</div>
```
n에 해당 요소가 몇 칸을 차지할지 정한다.

**📌 모든 요소는 위 구조를 따른 뒤 col-n 안에 넣어야 한다!!!**