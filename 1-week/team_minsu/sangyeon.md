# HTML, CSS 1주차

## Tag
### 1. 개념

- HTML은 Hypertext Markup Language의 줄임말로 하이퍼텍스트를 작성하기 위해 개발되었다.

- 프로그래밍에서 태그란 표현이나 어떤 기능의 수행을 지시하는 짧은 낱말  

<br>

### 2. 구조

HTML 요소(Element)는 시작 태그와 종료 태그 그리고 태그 사이에 위치한 content로구성됨
![태그 구조](https://media.prod.mdn.mozit.cloud/attachments/2014/11/14/9347/c07aa313dbdd667585430f4eca354dbd/grumpy-cat-small.png)

 <br>

### 3. 기본 태그
- 제목 표시 : h1~h6
- 문단 줄바꿈 : p,br
- 글자 굵게 : b,strong
- 글자 기울림 : em,l
- 글자 밑줄 : u
- 글자 취소선 : s,del
- 큰 글자 표시 : big
- 위 첨자 아래 첨자 : sup,sub
- 형광팬 : mark
- 수평선 : hr	

- 순서가 있는 목록 : ol >li
- 순서가 없는 목록 : ul >li

- 외부 링크 나 파일 열기 : a
<br>

### 4. P vs Span vs Div
div,p태그와 span 태그 차이
- p,div 태그 : 블록 요소
- span 태그 : 인라인 요소
-  p와 div 태그는 span을 하위 태그로 사용 가능, 그러나 반대는 불가능

P태그와 div 태그 차이
- p 태그 : 문자 정보를 입력하는 단락
- div 태그 : 문자 정보를 입력하는 기능도 있지만, 실제 용도는 html 문서의 영역별 구분
- div 태그는 p 태그를 하위태그로 사용 가능, 그러나 반대는 불가능
<br>

### 5. CSS 적용 우선순위
1. !important Style
2. inline Style
3. ID Selector Style
4. Class Selector Style
5. Tag Selector Style
<br><br><br>

## Semantic Tag
### 1. 개념
- 사이트의 구조(레이아웃)을 설계하기 위한 태그로, HTML의 구조를 설계하는데 있어 태그에 의미를 부여 함으로써 사이트의 구조를 파악하기 용이할 수 있도록 도와주기 위해 만들어진 태그
<br>

### 2. 장점
 1.	SEO 최적화에 유리
 2.	웹 접근성에 효율적
 3.	유지보수의 용이성
<br>

### 3. 대표적인 시멘틱 태그
1.	Header : 페이지 제목 or 소개 내용
2.	Nav : 메뉴 혹은 목차
3.	Aside : 사이드바 
4.	Main : 주 콘텐츠 영역
5.	Section : 구체적인 시멘틱 태그가 없는 문서의 독립적인 영역을 나타냄
6.	Article  : 게시글, 블로그 등 그 자체로 의미가 있는 웹사이트의 부분이며 독립적으로 배포 또는 재사용되도록 의도된 문서
7.	Footer : 일반적으로 섹션의 작성자에 대한 정보,저작권 데이터 등등
<br><br><br>

## Attribute

### 1. 구조
- 속성은 HTML 여는 태그 뒤에 한 칸 공백을 두고 입력한다.
- 속성은 속성명, 등호, 따옴표, 속성값 순서로 구성된다.
<br>

![속성 구조](https://dasima.xyz/wp-content/uploads/2019/01/HTML-attribute-use-1.png)
<br>

### 2. 속성 부여시 주의 사항
1.	요소 이름 다음에 바로 오는 속성은 요소 이름과 속성 사이에 공백으로 구분해야함.
2.	하나 이상의 속성들이 있는 경우엔 속성 사이에 공백이 있어야 함
3.	속성은 이름과 값으로 구분 됨
4.	이름 다음엔 등호를 사용하며 속성 값은 열고 닫는 따옴표로 묶여져야 함
<br>

### 3. 속성 선택자
- 특정 속성을 가진 요소 선택 ( 요소[attribute]{ } )
```html
ex) <p class>안녕</p>
```
- 특정 속성과 특정 속성값을 가진 요소 선택 ( 요소 [attribute="value"]{ } )
```html
ex) <p class="apple">안녕</p>
```
- 특정 속성과 특정 속성값만을 포함하는 요소 선택 (요소 [attribute~="value"]{ })
```html
ex) <p class~="apple">안녕</p>
    <p class="apple pie">안녕 </p> >>가능
    <p class="apple-pie">안녕 </p> >> 불가능 (하이폰 사용시, 불가능)
```
- 특정 속성과 특정 속성값을 포함하는 모든 요소 선택 (요소 [attribute*="value"]{ })
```html
ex) <p class>안녕</p>
    <p class="apple-pie">안녕 </p> >> 가능
    <p class="apple pie">안녕 </p> >> 가능
    <p class="asappleas">안녕 </p> >> 가능
```
- 특정 속성과 특정 속성값으로 시작하는 요소 선택 (요소 [attribute|="value"]{ })
```html
ex) <p class>안녕</p>
    <p class="apple">안녕 </p> >> 가능
    <p class="apple-pie">안녕 </p> >> 가능
    <p class="apple pie">안녕 </p> >> 불가능 (띄어쓰기 사용시, 불가능)
```
- 특정 속성과 특정 속성값으로 시작하는 모든 요소 선택 (요소 [attribute^="value"]{ })
```html
ex) <p class>안녕</p>
    <p class="apple">안녕 </p> >> 가능
    <p class="apple-pie">안녕 </p> >> 가능
    <p class="apple pie">안녕 </p> >> 가능
    <p class="applepie">안녕 </p> >> 가능
```
<br>

### 4. Attribute vs Property
- Attribute 
1.  Html 문서 안에서 사용됨
2.  정적인 속성을 갖고있음
- Property
1.  Html DOM 트리 안에서 사용됨
2.  동적인 속성을 갖고있음
<br><br><br>

## Grid와 Flex

### 1. Grid 와 Flex 차이
- flex 는 1차원으로 수평, 수직 영역  중 하나의 방향으로만 레이아웃을 나눌 수 있다.
- Grid는 2차원으로 수평과 수직을 동시에 레이아웃을 나눌 수 있다.
<br>

### 2. Felx 구조
<br>

![Flex 구조](https://studiomeal.com/wp-content/uploads/2020/01/02.jpg)
<br>

- 부모 요소인 .container 을 Flex Container 이라고 부르고,
- 자식 요소인 .item 을 Flex Item 이라고 부른다.
<br><br><br>

### 3. Grid 구조
<br>

![Grid 구조](https://studiomeal.com/wp-content/uploads/2020/01/03-2.jpg)
<br>

- 그리드 컨테이너 (Grid Container)<br>
display: grid를 적용하는, Grid의 전체 영역입니다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 된다.
- 그리드 아이템 (Grid Item)<br>
Grid 컨테이너의 자식 요소들입니다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 거예요.
- 그리드 트랙 (Grid Track)<br>
Grid의 행(Row) 또는 열(Column)
- 그리드 셀 (Grid Cell)<br>
Grid의 한 칸을 가리키는 말이에요. div 같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 됩니다.
- 그리드 라인(Grid Line)<br>
Grid 셀을 구분하는 선입니다.
- 그리드 번호(Grid Number)<br>
Grid 라인의 각 번호입니다.
- 그리드 갭(Grid Gap)<br>
Grid 셀 사이의 간격입니다.
- 그리드 영역(Grid Area)<br>
Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이에요.
<br>

그래서 주로 Grid를 이용하여 전체 레이아웃을 잡고, Flex를 이용하면 사이드 바나, nav같은 구조를 만듦
<br>
<br>
<br>

## Media Query
### 1.개념
- 미디어 쿼리는 반응형 웹을 만들기 위한 도구로 화면 해상도, 기기 방향 등의 조건으로 HTML에 적용하는 스타일을 전환할 수 있는 CSS3의 속성이다.
<br>

### 2. 가장 많이 쓰이는 문법
-	Min-width : 최소 너비
-	Max-width : 최대 너비
-	Min-height : 최소 높이
-	Max-height : 최대 높이
-	Aspect-ratio : 가로 세로 비율
-	Orientation : 방향
<br>

위 조건을 이용해 크기가 다른 각 기기마다 알맞게 보이는 웹페이지를 만들 수 있다 .또한, 가로로 되어있는지 세로로 되어있는지에 따른 웹페이지를 만들 수 있다.<br>

### 3. 논리 연산자
-	And : 다수의 미디어 특성을 조합할 때 and를 사용하여서 만들 수 있음
-	Not : 미디어 쿼리를 부정하여, 거짓일 때만 실행함. 반드시 미디어 유형을 지정해야 함
-	Only : 전체 쿼리가 일치할 때만 스타일을 적용함. 얘도 반드시 미디어 유형을 지정해야함
-	,(쉼표) : 다수의 미디어 쿼리를 하나의 규칙으로 조합할 때 사용. 논리 연산자 or의 역할로 하나의 쿼리만 참을 반환해도 규칙 전체가 참이 된다.
<br>

### 4. 미디어 유형
-  미디어별로 적용할 CSS를 따로 작성하는 것이므로 @media 속성 다음에 미디어 유형을 알려줘야 한다.
- 주로 screen을 이용하여 컴퓨터 스크린을 미디어 유형으로 정하지만, print나 다른 미디어 유형을 사용할 수 있다.
- 미디어 유형 종류
1. all : 모든장치
2. print :	인쇄 장치
3. screen :	컴퓨터 화면 장치 또는 스마트 기기의 화면
4. tv :	영상과 음성이 동시에 출력되는 장치
5. projection :	프로젝터 장치
6. handheld :	손에 들고다니는 소형 장치
7. speech :	음성 출력 장치
8. aural :	음성 합성 장치(화면을 읽어 소리로 출력해 주는 장치)
9. embossed :	점자 인쇄 장치(화면을 읽어 종이에 점자를 찍어내는 장치)
10. tty :	디스플레이 기능이 제한된 장치
11. braille :	점자 표시 장치
<br>


### 5. 대표적인 4개의 반응형 분기점
1. 낮은 해상도의 PC, 태블릿 가로 : ~1024px
2. 테블릿 가로 : 768px ~ 1023px
3. 모바일 가로, 태블릿 : 480px ~ 767px
4. 모바일 : ~ 480px