# `<table>`

- `<table>` : 테이블을 만들기 시작할 때 사용한다.
- `<tr>` : 하나의 행(가로줄)을 만들 때 사용한다. (table row)
- `<th>` : 하나의 열(칸)을 대표하는 셀을 만들 때 사용한다. (table header)
- `<td>` : 하나의 열(칸)의 데이터를 만들 때 사용한다. (table data)

<br />

## 테이블의 레이아웃에 영향을 주지 않고 묶을 때 사용하는 태그
- `<thead>` : 표의 머리글을 묶을 때 사용한다.
- `<tbody>` : 표의 본문을 묶을 때 사용한다.
- `<tfoot>` : 표의 바닥글을 묶을 때 사용한다. (총합, 요약 등)

```html
<table>
  <thead>
    <tr>
      <th> ID </th>
      <th> 이름 </th>
      <th> 취미 </th>
    </tr>
  </thead>
  
  <tbody>
    <tr>
      <td> lightixxx </td>
      <td> 라이틱스 </td>
      <td> 사진촬영 </td>
    </tr>
    <tr>
      <td> lalala </td>
      <td> 라라라 </td>
      <td></td> <!-- 빈칸이더라도 th의 개수와 맞춰준다 -->
    </tr>
  </tbody>
  
  <tfoot>
  </tfoot>
</table>
```

### table 태그 사용시 주의
`<th>`와 `<td>`의 개수 맞춰야 한다.
단, rowspan이나 colspan으로 확장이 된 경우는 생략 가능하다.

<br />

### 추가 attribute
- `rowspan="2"` : 숫자만큼 행을 병합한다.
- `colspan="2"` : 숫자만큼 열을 병합한다.
- `scope="col"` : 누구의 머리글 칸인지 명시한다. (col, colgroup, row, rowgroup)