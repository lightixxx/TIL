# Float
block 요소를 위로 띄워서 가로 배치하기 위한 속성이다. 요즘은 잘 사용하지 않지만 알아두면 좋다.


## float 속성을 주면 벌어지는 일
1. 자식요소에 float 속성을 주면 형제요소는 자식요소의 자리를 차지하게 되고, 부모요소는 float된 자식요소의 높이만큼 줄어든다.



2. float 속성을 주면 inline 요소나 inline-block 요소 모두 `display: block;` 이 된다.
   
   
   따라서 width, height, padding, margin 모두 쓸 수 있다. 단! 원래 block의 속성인 `width: 100%;` 가 되지는 않는다. (자동으로 생기던 margin이 생기지 않는다)


3. float 속성을 사용하면 block box들은 float를 없는 box 취급을 한다. 하지만, 텍스트나 이미지와 같은 inline 요소들은 float 요소들을 피해서 흐름을 갖고 작성된다.

<br />

## float 속성을 사용해서 와르르 멘션된 레이아웃을 고치는 방법

1. `parent { overflow: hidden; }`
  
    자식요소에 float를 사용하면 부모요소는 높이를 알지 못한다. 하지만, 부모요소에 `overflow: hidden;`을 주게되면 다시 자식요소만큼의 높이를 갖게된다.


2. `parent::after { content: ''; display: block; clear: both; }`

    HTML에는 존재하지 않는 가상 요소를 만들어서 clear 속성을 준다.