css정리

캐스케이딩
1) 순서에 의한 캐스케이딩
  • 나중에 적용한 속성값의 우선순위가 높음
2) 디테일에 의한 캐스케이딩
  • 더 구체적으로 작성된 선택자의 우선순위가 높음

박스 모델
1) margin과 padding의 차이
  • margin-left : border 바깥쪽에서 왼쪽에 여백을 만듦
  • padding-left : border 안쪽에서 왼쪽에 여백을 만듦 (공간이 여백을 포함한 크기로 변경되는 점 유의)
2) margin과 padding 작성 방법
  • top right bottom left 순서(시계 방향)로 한 줄에 작성 가능

Inline 요소의 특징
1) 줄바꿈 현상 없음
2) width / height 값 적용 불가
3) margin / padding / bottom 값 적용 불가

미디어쿼리
1) 미디어쿼리란
  • pc 뿐만 아니라 모바일과 태블릿에도 대응되는 웹사이트를 만들기 위해
  • 모바일에 대응되는 반응형 또는 적응형 웹사이트를 만들 때 사용되는 CSS 구문
2) 미디어쿼리 사용시 주의사항
  • 미디어쿼리가 제대로 작동하지 않는 문제가 발생할 수 있으므로 viewport로 너비와 배율을 설정해야 모바일 디바이스에서 의도한 화면을 볼 수 있음.
  • width=device-width : viewport의 가로폭 = 디바이스의 가로폭
  • initial-scale=1.0 : 비율은 항상 1.0

transition
1) :hover
  • 마우스를 특정 대상에 올렸을 때 미리 입력해둔 효과가 나타나게 해주는 기능이 있다.
2) 추가 transition 속성 옵션
  • ease:가장 많이 쓰이는 기본값 설정으로 자연스럽게 움직인다
  • ease-in: 천천히 시작 후 가속
  • ease-out: 빠르게 갔다가 천천히 멈춤
  • lenear: 처음부터 끝까지 같은 속도
