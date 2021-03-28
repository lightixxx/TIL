# prettier
협업시 여러 사람이 코드를 작성해도 일관된 규칙을 통해 한 사람이 코드를 짠 것 같이 정렬을 해준다.

1. cmd + , 를 눌러 설정 파일로 들어간다.
2. 저장을 할 때 형식이 맞춰지도록 format on save에 체크를 한다.
3. prettier config: Require Config에도 체크하는 것을 권장한다.
4. 에디터 설정(settings.json)에 `"editor.defaultFormatter": "esbenp.prettier-vscode"`를 추가해야 에러가 뜨지 않는다.

```json
{
  "semi": false, // 세미콜론은 사용하지 않겠다.
  "singleQuote": true, // 작은 따옴표는 사용하겠다.
  "endOfLine": "lf", // 마지막 한 줄의 new line을 만들어준다.
  "tabWidth": 2, // tab은 두 칸을 사용하겠다.
  "useTabs": false, // tab은 사용하지 않겠다.
}
```