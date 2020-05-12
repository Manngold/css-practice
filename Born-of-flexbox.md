# Born of flexbox

## Before flex box

### display

display에는 여러 속성들이 존재 한다.

1. block(div의 default 값)

-   div 태그의 display 기본 값으로 하나의 영역을 사용하기 때문에 다음 element는 자동적으로 줄 바꿈이 된다

2. none

-   박스가 생성되지 않음

3. inline(span의 default 값)

-   span 태그의 display 기본 값으로 줄 바꿈이 적용되지 않는다.
-   height, width 속성을 사용 할 수 없다

4. inline-block

-   외부는 inline으로 줄바꿈을 하지 않지만 내부적으로는 block 속성을 갖고 있어서 height, width 속성을 사용 할 수 있다.

하지만 위 속성과 `margin` 속성을 활용해서 반응형 웹사이트를 만들기는 쉽지 않았고, 이는 `flexbox`의 탄생 배경이 된다.
