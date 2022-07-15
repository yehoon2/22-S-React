CSS
- 요소 배치
1. 포지셔닝
static 기본값으로 페이지의 흐름대로 배치
relative 원래 위치를 기준으로 top bottom left right 속성값을 활용하여 그만큼 떨어진 곳에 배치
absolute 첫 부모 요소를 기준으로 흐름에서 벗어나 지정하고 싶은 곳에 배치
fixed 스크롤의 영향을 받지 않고 화면을 기준으로 지정한 곳에 배치

2. flex 속성을 활용하여 flex 박스 안 아이템들을 유연하게 배치
- flex-basis 
너비나 높이의 값을 입력하여 각 아이템을 똑같은 크기로 배치시키고 설정 값 보다 크기가 더 큰아이템의 경우에는 그대로 배치
- flex-grow
flex-basis 보다 더 크게 설정할지 정하는 속성으로 flex-basis를 제외한 여백 부분을 설정한 값의 비율로 설정
- flex-shrink
flex-grow와 주로 같이 사용하며 flex-basis의 값보다 작아질 수 있는지 결정하는 속성
- flex
세 가지 속성을 한 번에 설정하는 축약형 속성으로 flex-grow, flex-shrink, flex-basis 순으로 설정


