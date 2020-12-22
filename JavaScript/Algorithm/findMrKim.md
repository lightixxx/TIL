# 서울에서 김서방 찾기

## 문제설명
String형 배열 seoul의 element 중 'Kim'의 위치(x)를 찾아, '김서방은 x에 있다'는 String을 반환하는 함수, solution을 완성하세요. seoul에 'Kim'은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.

<br />

## 제한 사항
- seoul의 길이는 1이상, 1000 이하인 배열입니다.
- seoul의 원소는 길이 1이상, 20 이하인 문자열입니다.
- 'Kim'은 반드시 seoul 안에 포함되어 있습니다.

<br />

## 입출력 예
seoul - ["Jane", "Kim"]
return - "김서방은 1에 있다"

<br />

## 내 풀이
for 반복문을 사용해 seoul 배열을 모두 돌면서 'Kim'을 만나면 Index 값을 반환한다.
```jsx
function solution(seoul) {
	for (let i = 0; i < seoul.length; i++) {
		if (seoul[i] === 'Kim') return `김서방은 ${i}에 있다`
	}
}
```

<br />

## 다른 사람의 풀이
`indexOf()` 메서드를 사용해서 배열 내부를 모두 검사한 뒤 해당 객체가 위치하는 인덱스를 리턴했다.
```jsx
function solution(seoul){
  var idx = seoul.indexOf('Kim');
  return `김서방은 ${idx}에 있다`;
}
```

<br />

##### 출처
- [프로그래머스 level 1 서울에서 김서방 찾기](https://programmers.co.kr/learn/courses/30/lessons/12919)