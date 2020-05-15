# Flexbox

## Before flexbox

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

## After Flexbox

Flexbox의 탄생 이전에는 박스들을 컨트롤 하기 위해서 children들 각각에 속성을 주면서 박스의 위치를 컨트롤 했다.

Flexbox가 나온 뒤에는 children들을 감싸고 있는 부모 박스의 속성을 설정하면서 children들을 한번에 컨트롤 할 수 있게 되었다.

```
<div id="parent">
    <div class="children">1</div>
    <div class="children">2</div>
    <div class="children">3</div>
</div>
```

`#parent{display: flex;}` 속성을 넣어주면 parent의 flexbox 속성 컨트롤을 통해서 children들을 컨트롤 하게 된다.

`display: flex`로 설정하는 순간 children들의 display 속성은 inline-block로 설정이 되고 배치 방향은 row가 된다

### flex-direction

`flex-direction`은 flexbox의 main axis와 cross axis를 설정 할 수 있다.

`flex-direction : row`는 main axis : row, cross axis : column

`flex-direction : column`는 main axis : column, cross axis : row

### justify-content

main axis에 존재하는 children들의 위치를 컨트롤 한다

### align-content

flexbox가 줄 바꿈을 하게 될 경우 설정을 진행한다.

### align-items

cross axis에 존재하는 children들의 위치를 컨트롤

### align-self

`align-items`처럼 cross axis의 위치를 변경하지만 하나의 박스에 대해서 위치를 컨트롤 하는 것이다.

```
.children:nth-child(2) {
    align-self: center;
}
```

이렇게 하나의 박스에 대해서 위치를 설정 할 수 있다.

### flex-wrap

flexbox 안의 children들이 설정된 width가 있고, children이 무수히 많다면 어떻게 될까?

자동적으로 줄 바꿈을 하면서 설정된 width를 유지한다고 생각하겠지만, width를 줄이면서 같은 줄을 유지한다

이때 `flex-wrap` 속성을 사용한다 값은 `wrap`, `nowrap`이 존재하는데 `wrap`을 하게되면 기존 children의 width를 유지하기 위해서 줄 바꿈을 한다

반대로 `nowrap`는 default 값으로 children의 width를 변경하면서 줄을 유지한다

### flex-shrink

`flex-shrink`는 flexbox의 children이 `nowrap`일 경우 width가 줄어드는 비율을 결정한다

### flex-grow

`flex-grow`는 flexbox의 children이 여백을 차지하는 비율을 결정한다.

-   flex-shrink와 flex-grow는 `nth-child()`를 사용해서 값을 설정 할 수 있다.

### flex-basis

`flex-basis`는 flex-direction에 따라 너비 혹은 높이를 설정해준다
