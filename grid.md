# Grid

## Before Grid

Grid가 탄생하기 전에 flexbox를 활용해서 Grid(격자무늬) 배열을 만들기란 쉽지 않았다. 고려할 사항이 너무 많기 때문이다.

box의 배치, 비율, 간격, 줄바꿈이 발생 할 경우 이전 row와의 간격 등, 신경 쓸 요소가 너무 많았다

따라서 grid가 탄생했는데 flexbox와 마찬가지로 parent를 활용해서 child를 컨트롤한다

### grid-template-column, grid-template-row

grid의 column과 row를 설정하는 속성이다.

column과 row의 갯수만큼 너비를 설정해주면 자동적으로 줄 바꿈을 하면서 box들이 배치된다.

### gap

grid에서 box간 간격을 설정할때 사용하는 속성이다.

### grid-template-areas

gird를 활용해서 전체적인 template를 작성하는 방법이다

string값을 넣어서 해당 구역이 어떤 역활을 하는지 적어주고 해당 child에 `grid-area` 속성 값을 설정해주면 적용이 된다.

### repeat()

column과 row를 설정 할 때, 연속되는 부분을 개별적으로 설정하지 않고 `repeat()`을 활용해서 한 번에 설정할 수 있다

-   repeat(반복 횟수, 크기)

이렇게 설정을 해주면 반복되는 횟수 많큼 해당 너비로 자동적으로 설정이 된다.

### grid-(column/row)-start, grid-(column/row)-end

grid box가 시작되고 끝나는 line을 결정해준다.

예를들어, column이 `repeat(4, 200px)`의 속성을 갖고 있을 때, 어떤 child grid box가

4개의 연속되는 모든 영역을 차지하려면 `grid-column-start: 1; grid-column-end: 5;`를 활용해서 모든 영역을 차지할 수 있다

start값은 grid box가 시작하는 지점 end 값은 끝나는 지점이고 박스의 line을 기준으로 설정이 된다

### grid-row, grid-column

`grid-column-start/end`를 사용한다면 각각의 속성을 사용하면 start와 end 속성을 따로 설정을 해야 한다

하지만 `grid-column`, `grid-row`를 사용하면 start와 end 속성을 한 번에 정의 할 수 있다

기존에 시작부터 끝까지 속성을 정의하려면

```
grid-column-start: 1;
grid-column-end: 5;
```

이런 방식으로 입력을 해야 했지만, grid-column과 grid-row를 활용해서

`grid-column : 1 / 5;` 로 변경 할 수 있게 되었다.

### fr(fraction)

fr은 grid 영역에서 cell이 최대한 차지하는 공간의 단위이다. 비율에 따라서 자동으로 조절이 된다

### grid-template

이 속성을 활용해서 areas, column, row, line naming 등을 설정 할 수 있다.
