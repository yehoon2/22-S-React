# transform
: 특정 요소의 크기나 형태 등 스타일이 바뀌는 것
1 2차원 변형
- 수평이나 수직으로 웹 요소 변형
- 크기나 각도만 지정하며 2차원 좌표를 사용
2 3차원 변형
- x축과 y축에 원근감을 추가
- z축은 앞뒤로 이동, 보는 사람 쪽으로 다가올 수록 값이 커짐
* translate > 이동, scale > 확대, rotate > 회전, skew > 비틀기
# transition
* ease, linear, ease-in, ease-out, ease-in-out
# animation
- @keyfraomes 를 이용해 애니메이션 정의, from과 to를 이용
# 반응형 웹
- 뷰포트 지정하기
~~~ html
<meta name="viewport" content="속성1=값1", ...>
~~~
사용법 : 뷰포트의 너비를 스마트폰 화면 너비에 맞추고 초기 화면 배율을 1로 지정
# 미디어 쿼리
: 접속하는 장치(미디어)에 따라 특정한 CSS 스타일을 사용하는 방법
- @media 속성을 사용해 특정 미디어에서 어떤 CSS를 적용할 것인지 지정
- <style> 태그 사이에 사용
* 조건
1 웹 문서의 가로 너비와 세로 높이(뷰포트)
: 실제 웹 문서 내용이 나타내는 영역의 너비와 높이를 조건으로 사용
2 단말기의 가로 너비와 세로 높이
: 대부분의 단말기 해상도와 실제 브라우저의 너비가 다르다는 점에 주의
3 화면 회전
: 스마트폰이나 태블릿에서 기기를 가로나 세로로 돌려보는지 확인
ex) 너비에 따라 백그라운드 사진 변경
~~~ html
<style>
    body {
      background: url(bg0.jpg) no-repeat fixed;
      background-size: cover;
    }
    @media screen and (max-width:1024px) {
      body {
        background: url(bg1.jpg) no-repeat fixed;
        background-size: cover;
      }
    }
</style>
~~~
# 그리드 레이아웃
- 반응형 웹 디자인에서 웹 문서 요소를 배치하는 기준
- 웹 사이트 화면을 여러 개의 칼럼(column)으로 나눈 후 웹 요소를 배치
- 화면을 규칙적으로 배열하므로 레이아웃을 일관성 있게 유지할 수 있음
특징 : 시각적으로 안정된 디자인 / 업데이트가 편한 웹 디자인 구성 / 요소를 자유롭게 배치
# 플렉스 박스 레이아웃(플렉서블 박스 레이아웃)
- 그리드 레이아웃을 기본으로, 플렉스 박스를 원하는 위치에 배치하는 것
- 여유 공간에 따라 너비나 높이, 위치를 자유롭게 변형할 수 있음
1 플렉스 컨테이너(부모 박스) : 플렉스 박스 레이아웃을 적용할 대상을 묶는 요소
2 플렉스 항목(자식 박스) : 플렉스 박스 레이아웃을 적용할 대상
3 주축(main axis) : 플렉스 컨테이너 안에서 플렉스 항목을 배치하는 기본 방향으로 왼쪽에서 오른쪽 수평 방향
으로 배치
4 교차축(cross axis) : 주축과 교차하는 방향으로 위에서 아래 수직 방향으로 배치
~~~ html
<style>
    .container {
      width:700px;
      display:flex; /* 플렉스 컨테이너 지정 */
      background-color:#eee;
      border:1px solid #222;
      margin-bottom:30px;
      flex-direction: row;
      flex-wrap: wrap;
      }
      .box {
      padding:5px 45px;
      margin:5px;   
	  	width:80px;
      background-color:#222;   
      }
      p {
      color:#fff;
      text-align: center;
      }
</style>
~~~
# CSS 그리드 레이아웃
- 플렉스 박스 레이아웃은 주축/교차축 개념이 있지만 css 그리드 레이아웃은 양쪽 방향 모두 사용
(플렉스 그리드 레이아웃은 1차원 ,CSS 그리드 레이아웃은 2차원이라고도 함)
- 줄(row)과 칼럼(column)으로 화면을 구성하고, 줄 사이의 여백, 칼럼 사이의 여백을 조절.
1 그리드 라인을 사용해 배치하기
- css 그리드 레이아웃에는 눈에 보이지 않는 그리드 라인이 포함되어 있음
- 그리드 라인을 사용해 그리드 항목을 배치할 수 있음
~~~ html
<style>
  # wrapper {
    width: 700px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 100px)
    }
~~~
~~~ html
<style>
  .box1 {
    background-color:#3689ff;
    grid-column:1/4;
    }
  .box2 {
    background-color:#00cf12;
    grid-row:2/4;
    }
  .box3 {
    background-color:#ff9019;
    grid-column:2/4;
    grid-row:2/3; /* = grid-row-start:2; */
    }
  .box4 {
    background-color:#ffd000;
    grid-column-start:3; /* = grid-row-start:3; */
    }
</style>
~~~
2 템플릿 영역을 만들어 배치하기
- grid-area 속성을 사용해 템플릿 영역을 만든 후 배치
ex) box5 ~ box8까지 네 개의 템플릿 영역을 만든 후 배치
1) 템플릿 영역 만들기
~~~ html
<style>
  .box5 {
    background-color:#3689ff;
    grid-area: box5;
    }
  .box6 {
    background-color:#00cf12;
    grid-area:box6;
    }
  .box7 {
    background-color:#ff9019;
    grid-area:box7;
    }
  .box8 {
    background-color:#ffd000;
    grid-area:box8;
    }
</style>
~~~
2) 템플릿 영역 배치하기
~~~ html
<style>
  #wrapper3{
    width:700px;
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    grid-template-rows:repeat(3, 100px);
    grid-template-areas:
    "box5 box5 box5"
    "box6 box7 box7"
    "box6 . box8";
    }
</style>
~~~