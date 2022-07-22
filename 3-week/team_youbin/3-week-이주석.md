## 자바스크립트 (JavaScript)

### 자바스크립트로 무엇을 할까

- 웹 요소 제어
    1) 웹 요소를 가져와서 필요에 따라 스타일을 변경하거나 움직이게 할 수 있음
    2) 웹 사이트 UI 부분에 많이 활용
    3) 예) 마우스 포인터를 올렸을 때 펼쳐지는 메뉴, 한 화면에서 탭을 눌러 내용만 바뀌도록 하는 컨텐츠
    
- 다양한 라이브러리 사용 가능
    1) 웹을 중심으로 하는 서비스가 늘어나면서 브라우저에서 처리해야 할 일이 늘어남 -> 라이브러리와 프레임워크가 계속 등장
    2) 예) 시각화를 위한 d3.js, 머신러닝을 위한 tensorflow.js, DOM 조작을 위한 jQuery 등
    3) 예) 웹 애플리케이션 개발을 위한 React, Angular, Vue 등
    
- 웹 애플리케이션 제작
    1) 최근의 웹 사이트는 사용자와 실시간으로 정보를 주고 받으며 애플리케이션처럼 동작
    2) 예) 온라인 지도의 길찾기 서비스, 데이터 시각화 서비스, 공개된 API를 활용한 다양한 서비스

- 서버 구성 및 서버용 프로그램 제작 가능
    node.js : 프론트엔드 개발에 사용하던 자바스크립트를 백엔드 개발에서 사용할 수 있게 만든 프레임워크


### 웹 브라우저가 자바스크립트를 만났을 때

- 웹 문서 안에 자바스크립트 작성하기
    1) <script> 태그와 </script> 태그 사이에 자바스크립트 소스 작성
    2) 자바스크립트 소스가 있는 위치에서 실행됨.
    3) 웹 문서 안의 어디든 위치할 수 있지만, 주로 </body> 태그 앞에 작성    
    
    ```html
    (...생략...)

    <body>
        <h1 id="heading">자바스크립트</h1>
        <p id="text">위 텍스트를 클릭해 보세요</p>

        <script>
            var heading = document.querySelector('#heading');
            heading.onclick = function() {
                heading.style.color = "red";
            }
        </script>
    </body>

    (...생략...)
    ```

- 외부 스크립트 파일 연결해서 작성하기
    자바스크립트 소스르 별도의 파일(*.js)로 저장한 후 웹 문서에 연결

    ```js
    // 파일명 : change-color.js
    var heading = document.querySelector('#heading');
    heading.onclick = function() {
        heading.style.color = "red";
    }
    ```

    ```html
    (...생략...)

    <body>
        <h1 id="heading">자바스크립트</h1>
        <p id="text">위 텍스트를 클릭해 보세요</p>

        <script src="change-color.js"></script>
    </body>

    (...생략...)

### 자바스크립트 스타일 가이드

- 자바스크립트 소스를 작성할 때 지켜야 할 기본 규칙
    1) 코드르 보기 좋게 들여쓴다.
    2) 세미콜론으로 문장을 구분한다.
    ```js
    var n = 10                  // 권장하지 않음
    var n = 10;                 // 권장함
    var n = 10; var sum = 0;    // 권장하지 않음
    ```
    3) 공백을 넣어 읽기 쉽게 작성한다.
    ```js
    var sum=num+10;             // 권장하지 않음
    var sum = num + 10;         // 권장함
    ```
    4) 코드를 설명하는 주석을 작성한다.
    한 줄 주석 작성 방법
    ```js
    var today = new Date();     // 현재 날짜 가져오기
    var h = today.getHours();   // 시간 추출하기
    ```
    여러 줄 주석 작성 방법
    ```js
    /* 현재 날짜를 가져와
       시와 분, 초로 추출하고
       화면에 표시하는 스크립트
    */
    function startTime() {............}
    ```
    5) 식별자는 정해진 규칙을 지켜 작성한다.

### DOM 이란?

- 문서 객체 모델(Document Object Model)
    객체 지향 모델로써 구조화된 문서를 표현하는 방식
    
- HTML 문서에 대한 인터페이스
    DOM은 XML이나 HTML문서의 프로그래밍 인터페이스
    DOM은 문서의 구조화된 표현을 제공하여 프로그래밍 언어가 문서 구조, 스타일, 내용 등을 변경할 수 있도록 합니다.
    
- DOM의 종류
    Core DOM : 모든 문서 타입을 위한 DOM 모델
    HTML DOM : HTML 문서를 위한 DOM 모델
    XML DOM : 문서를 위한 DOM 모델

- HTML DOM
    HTMl 문서를 조작하고 접근하는 표준화된 방법
    모든 HTMl 요소를 HTMl DOM을 통해 접근 가능

- XML DOM
    XML 문서에 접근하여 그 문서를 다루는 표준화된 방법을 정의
    모든 XML 요소는 XML DOM을 통해 접근 가능

- Document 객체
    Document 객체는 웹 페이지를 의미합니다.
    웹 페이지에 존재하는 HTML요소에 접근하고자 할 때는 반드시 Document 객체부터 시작해야 합니다.

- Document 메소드
    HTML 요소와 관련된 작업을 도와주는 다양한 메소드 제공
        • HTML 요소의 선택
            document.getElementById()               // 해당 아이디의 요소를 선택
            document.getElementsByClassName()       // 해당 클래스에 속한 요소를 모두 선택
            document.getElementsByName()            // 해당 name 속성값을 가지는 요소를 모두 선택
            document.querySelectorAll()             // 해당 선택자로 선택되는 요소를 모두 선택
            document.querySelector()                // 해당 선택자로 선택되는 요소를 1개 선택
        • HTML 요소의 생성
            document.createElement()                // 지정된 HTML 요소를 생성
            document.write()                        // HTML 출력 스트림을 통해 텍스트를 출력
        • HTML 이벤트 핸들러 추가
            요소.onclick = function(){}             // 마우스 클릭 이벤트와 연결될 이벤트 핸들러
        • HTML 객체의 선택


### Node 객체

- 노드(Node)와 노드 트리
    HTML DOM에서 정보를 저장하는 계층적 단위

    노드 트리는 노드들의 집합으로, 노드 간의 관계를 나타낸다.

    자바스크립트에서는 HTML DOM을 이용하여 노드 트리에 포함된 모든 노드에 접근할 수 있다.

- 노드의 종류
    • 문서 노드(document node) : HTML 문서 전체를 나타내는 노드
    • 요소 노드(element node) : 모든 HTML 요소는 요소 노드로, 속성 노드를 가질 수 있는 유일한 노드
    • 주석 노드(comment node) : HTML 문서의 모든 주석은 주석 노드   
    • 속성 노드(attribute node) : 모든 HTML 요소의 속성은 속성 노드이며, 요소 노드에 관한 정보를 가진다.
                                하지만 해당 요소 노드의 자식 노드에는 포함되지 않는다.
    • 텍스트 노드(text node) : HTML 문서의 모든 텍스트는 텍스트 노드


### 이벤트(Event)

- 이벤트(Event)란?
    웹 브라우저가 알려주는 HTML 요소에 대한 사건의 발생
    자바스크립트는 발생한 이벤트에 반응하여 특정 동작을 수행할 수 있다.

- 이벤트 타입
    마우스 이벤트
        • click : 사용자가 HTML 요소를 클릭할 때 이벤트가 발생합니다.
        • dbclick : 사용자가 HTML 요소를 더블클릭할 때 이벤트가 발생합니다.
        • mousedown : 사용자가 요소 위에서 마우스 버튼을 눌렀을 때 이벤트가 발생합니다.
        • mousemove : 사용자가 요소 위에서 마우스 포인터를 움직일 때 이벤트가 발생합니다.
        • mouseover : 마우스 포인터가 요소 위로 옮겨질 때 이벤트가 발생합니다.
        • mouseout : 마우스 포인터가 요소를 벗어날 때 이벤트가 발생합니다.
        • mouseup : 사용자가 요소 위에 놓인 마우스 버튼에서 손을 뗄 때 이벤트가 발생합니다.

    키보드 이벤트
        • keydown : 사용자가 키를 누르는 동안 이벤트가 발생합니다.
        • keypress : 사용자가 키를 눌렀을 때 이벤트가 발생합니다.
        • keyup : 사용자가 키에서 손을 뗄 때 이벤트가 발생합니다.

    문서 로딩 이벤트
        • abort : 문서가 완전히 로딩되기 전에 불러오기를 멈췄을 때 이벤트가 발생합니다.
        • error : 문서가 정확히 로딩되지 않았을 때 이벤트가 발생합니다.
        • load : 문서 로딩이 끝나면 이벤트가 발생합니다.
        • resize : 문서 화면 크기가 바뀌었을 때 이벤트가 발생합니다.
        • scroll : 문서 화면이 스크롤되었을 때 이벤트가 발생합니다.
        • unload : 문서에서 벗어날 때 이벤트가 발생합니다.

    폼 이벤트 
        • blur : 폼 요소에 포커스를 잃었을 때 이벤트가 발생합니다.
        • change : 목록이나 체크 상태 등이 변경되면 이벤트가 발생합니다. ```<input>, <select>, <textarea> 태그에서 사용합니다.```
        • focus : 폼 요소에 포커스가 놓였을 때 이벤트가 발생합니다. ```<label>, <select>, <textarea>, <button> 태그에서 사용합니다.```
        • reset : 폼이 리셋되었을 때 이벤트가 발생합니다.
        • submit : submit 버튼을 클릭했을 때 이벤트가 발생합니다.
