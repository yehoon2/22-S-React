[ HTML & CSS 정리 ]

- <input> 에서 type 지정 및 세부 사항
value : 입력창에 나오는 값을 작성한다.
autofocus : 처음 페이지에 들어왔을 때 커서가 놓인다.

type 종류 : text, password,
checkbox, number, range, 
image, radio, file, 
submit, reset, 
hidden


- 표 작성하기
<table>을 이용하여 작성한다.

<th>
테이블의 헤더

<tr>
테이블의 행 

<td>
테이블의 열


- 시맨틱 태그 정리
<header>
페이지나 구획의 제목 역할을 하는 요소들을 두는데 사용한다.
로고와 제목, 검색창 등이 들어간다.

<nav>
링크들을 포함하는 태그.
주로 페이지의 메뉴들이나 색인 등에 사용된다.

<footer>
페이지나 구획의 최하단에 보여지는 푸터에 사용된다.
페이지의 주인 연락처 및 저작권 정보 등이 들어간다.

<main>
페이지의 주요 내용이 들어가는 곳이다.
페이지에서 하나만 존재해야 한다.

<aside>
사이드바 등 주요 내용과 간접적으로 연관된 컨텐츠를 포함한다.

<section>
페이지의 컨텐츠를 일정 단위의 구획으로 나누는데 사용한다.
더 작은 단위의 컨테이너는 <div>를 사용합니다.

<article>
페이지 내에서 재사용될 수 있거나 페이지로부터 독립적인,
즉 다른 페이지에서도 사용될 수 있는 컨텐츠에 사용한다.
기사나 블로그 포스트, 댓글 등에 사용한다.


- 스타일 우선순위
Q. 나중에 쓰여진 값이 먼저 적용?
A. 얼마나 중요한가에 따라, 소스 순서에 따라, 얼마나 한정 지을 수 있는가에 따라! 
: !important > in-line > id > class > type 순


- Margin box 모델링 순서
: top > right > bottom > left 순

margin 중첩 현상 : 요소를 세로로 배치할 경우, margin이 만날 때 값이 큰 쪽으로 겹쳐진다.


- 주석 달기
Window : control + ?
macOS : command + ?




