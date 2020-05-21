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

### justify-items, align-items

grid의 item들은 기본적으로 `stretch` 속성을 갖고 item을 늘려서 cell의 값을 채웁니다

이때 수평은 `justify-items`, 수직은 `align-items`를 활용하여 컨트롤 합니다.

### place-items

`justify-items`와 `align-items`속성을 한 번에 컨트롤 할 수 있도록 해줍니다.

### justify-content, align-content

`justify-content`와 `align-content`는 grid의 item들을 컨트롤 하는 것이 아니라 grid 자체의 위치를 변경합니다.

`justify-content`는 수평 위치, `align-content`은 수직 위치를 컨트롤 합니다

### place-content

`justify-content`와 `align-content`속성을 한 번에 컨트롤 할 수 있도록 해줍니다.

### grid-auto-rows/columns

`grid-template-columns/rows`로 설정된 갯수보다 cell들이 많아질 경우 많아진 cell에 대해서 속성이 적용되지 않는다

따라서 초과된 갯수에 대한 cell의 속성을 정의하기 위해서 `grid-auto-rows/columns` 속성을 사용하면 초과된 갯수에 대한 cell의 속성 값을 설정 할 수 있다

### grid-auto-flow

초과된 cell을 어떻게 배치할 것인가에 대한 속성이다 `column row dense` 등의 속성이 존재한다

### minmax

cell들이 갖는 최소 크기와 최대 크기를 설정할 수 있다.

`grid-template-columns/rows`에서 설정 할 수 있다.

cell의 너비는 항상 min 값을 유지하고 최대 max값을 갖는다.

이때 min 값을 유지하기 위해 column과 row에서 설정해둔 cell의 갯수를 무시 할 수 있다

### auto-fit/fill

line에서 cell의 상태를 결정해준다

auto-fit은 해당 라인이 빈 공간이 발생하지 않게 맞추기 위해서 cell의 너비를 늘리거나 줄이면서 line을 채운다.

auto-fill은 라인이 다 채워지지 않고 빈 공간이 생기더라도 cell의 크기를 유지한다.

새로운 cell이 추가되는 상황

auto-fit은 새로운 cell을 넣고 모든 cell의 너비를 조정한다

auto-fill 전체 cell의 크기를 유지하면서 cell을 추가한다.

### min-content, max-content

cell안의 content 크기에 따른 cell의 크기 적용 기법이다

min-content : content를 줄일 수 있는한 최대한 작게 줄인다

max-content : content를 건드리지 않고 최소한의 크기를 유지한다

이 속성과 repeat, minmax 속성을 활용하면 손쉽게 반응형 디자인을 구현 할 수 있게 된다.

`grid-template-columns : repeat(5, minmax(max-content, 1fr))`

이 설정을 해석하면

line에 5개의 cell이 존재하는데 cell의 크기는 최소, 최대 크기가 설정되어 있다

최소 크기는 cell의 content를 건드리지 않고 최소한의 크기를 유지하고

최대 크기는 1fr의 크기만큼 차지한다
