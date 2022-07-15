# HTML

## HTML 이란?

[HTML: Hypertext Markup Language | MDN](https://developer.mozilla.org/ko/docs/Web/HTML)

HTML : Hypertext Markup Language 웹의 기초적인 구성 요소. 웹 컨텐츠의 의미와 구조를 정의할 때 사용.
Hypertext란 웹페이지를 다른 페이지로 연결하는 링크.

## HTML 의 요소

- Element
  - Opening tag
  - Content
  - Closing tag

## Semantic tag 란?

[HTML Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)

Semantic element 는 자신의 의미를 브라우저와 개발자 모두에게 명확하게 설명하는 요소.

non-semantic tags

```html
<div></div>

<span></span>
```

위의 태그들은 자신의 contents에 대해 설명해주지 않음.

semantic tags

```html
<main></main>

<aside></aside>

<nav></nav>
```

위의 태그들을 보면 어떤 내용이 들어갈지 유추할 수 있음

## Attributes

[HTML basics - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)

속성이란 실제로는 표시되지 않는 추가적인 정보를 담는다.

```html
<p class="new-string">Hello World</p>
```

예를 들어 위처럼 class 속성을 이용해 나중에 해당 element 를 특정할 수 있으며 이때 속성은 식별자의 역할을 한다. 위에서 class 는 Attribute name(속성 이름)이며 뒤에 오는 new-string 은 Attribute value 이다.

### 속성이 항상 가져야 하는 것

- 요소 이름 (이나 전 속성)과 속성 이름 사이에 공간.
- 속성 이름 뒤에는 등호가 따라와야한다.
- 속성 값은 따옴표로 감싸져야한다.

# Layout - Flex & Grid

## Flex

[이번에야말로 CSS Flex를 익혀보자](https://studiomeal.com/archives/197)

Flex (Flexible box, Flexbox)는 레이아웃 배치 전용 기능으로 고안되었기에 float, inline-block 을 이용하던 방식과 비교하여 강력하고 편리한 기능 사용 가능.

```html
<div class="container">
  <div class="item">helloflex</div>
  <div class="item">abc</div>
  <div class="item">helloflex</div>
</div>
```

부모 요소인 div.container는 Flex Container 라고 한다. 자식요소인 div.item 들은 Flex Item 이라고 부른다.

“컨테이너가 Flex의 영향을 받는 전체 공간이고, 설정된 속성에 따라 각각의 아이템들이 어떤 형태로 배치되는 것"

Flex의 속성에는 컨테이너에 적용하는 속성과 아이템에 적용하는 속성으로 나뉜다.

## Grid

[이번에야말로 CSS Grid를 익혀보자](https://studiomeal.com/archives/533)

Flex 와 Gird의 차이점:

- Flex는 한 방향 레이아웃 시스템 (1차원)

- Grid는 두 방향(가로-세로) 레이아웃 시스템(2차원)

- **그리드 컨테이너 (Grid Container)**
  - display: grid를 적용하는, Grid의 전체 영역. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬됨.
- **그리드 아이템 (Grid** **Item)**
  - Grid 컨테이너의 자식 요소. Grid 규칙에 의해 배치
- **그리드 트랙 (Grid Track)**
  - Grid의 행(Row) 또는 열(Column)
- **그리드 셀 (Grid Cell)**
  - Grid의 한 칸을 가리키는 말. <div>같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸”.
- **그리드 라인(Grid Line)**
  - Grid 셀을 구분하는 선.
- **그리드 번호(Grid Number)**
  - Grid 라인의 각 번호.
- **그리드 갭(Grid Gap)**
  - Grid 셀 사이의 간격.
- **그리드 영역(Grid Area)**
  - Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합.

# Media Qurey

[Using media queries - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)

## Media Query

미디어 쿼리란 사용자가 사용하는 디바이스의 유형과 어떤 특성이나 수치에 따라서 웹이나 앱의 화면을 조정할 때 사용됨

미디어 쿼리는 다음과 같은 상황에 사용됨.

- CSS 에서 @media, @import 의 at-rule들을 사용하여 특정 조건에 따라 스타일을 변경할 때
- style, link, source 의 기타 HTML 요소에 media= 속성을 사용해 특정할 때
- 미디어 상태를 판별하고 관측할 때 Window.matchMedia( ), MediaQueryList.addListener( ) 메서드를 JS 에서 사용.

### 구문

미디어 유형(optional), 미디어 특성(자유로움)의 표현식으로 이루어짐. 논리 연산자를 사용해 다양한 수의 쿼리를 결합할 수 있음. 이는 대소문자를 구분하지 않음.
