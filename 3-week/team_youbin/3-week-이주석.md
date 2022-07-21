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