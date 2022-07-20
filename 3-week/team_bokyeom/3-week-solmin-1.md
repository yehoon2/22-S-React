# 2022.7.19일 Cow 프론트엔드 공부

---

- [x]  인프런 React강의 Section0~2
- [x]  MPA,SPA,SSR,CSR 조사

---

[](https://www.inflearn.com/course/%EC%B2%98%EC%9D%8C-%EB%A7%8C%EB%82%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8#curriculum)

JavaScript의 자료형

- Number
- String
- Boolean
- Null
- Undefined
- 정의되지 않음, 변수를 선언만 하고 데이터 입력 X
- Array
- 배열, 다양한 자료형의 변수가 함께 들어갈 수 있음
- Object
- 객체를 다루기 위한 자료형
- 객체란 key와 value로 이루어진 쌍의 집합
- 객체 안에 객체가 또 있을 수 있음

JS의 연산자(Operator)

- 대입 연산자(Assignment operator)
- 항상 오른쪽에서 왼쪽 방향으로 흐름이 흘러감
- 수학의 ‘=’과는 의미가 다름
- 산술 연산자(Arithmetic operator)
- 덧셈(+),뺄셈(-),곱셈(*),나눗셈(/),나머지를구하는연산자(%),지수연산자(***)
- postfix방식 : a++
- prefix방식 : ++a
- 관계 연산자(Relational opertor)/비교 연산자(Comparison operator)
- <,>,≤,≥
- 동등 연산자(Equality opertor)
- ==,≠
- 일치 연산자(Strict equality operator)
- 엄격하게 동일한지 체크함
- 변수의 값뿐만 아니라 자료형도 같은지 체크함
- ===(값과 자료형이 모두 같다),≠=(값이나 자료형이 같지 않다)
- 이진 논리 연산자(Binary logical operator)
- &&(and)(모두 true일 경우에만 true)
- ||(or)(둘 중 하나라도 true일 경우 true)
- 조건부 연산자(Conditional operator)/삼항 연산자(Ternary operator)
- 조건식 ? true일 경우 : false일경우

리액트(React)

사용자 인터페이스를 만들기 위한 JavaScript library

라이브러리란? - 자주 사용되는 기능들을 정리해 모아놓은 것

사용자 인터페이스(User Interface, UI) - 사용자와 컴퓨터 프로그램이 서로 상호작용하는 것을 조정함

사용자 인터페이스를 만들기 위한 기능 모음집 - UI 라이브러리(리액트도 포함)

장점

1. 빠른 업데이트 & 렌더링 속도
- 빠른 업데이트 위해 Virtual DOM(가상의 돔) 사용
- 업데이트 = DOM이 수정된다
- Virtual DOM에서는 State Change가 발생하면 업데이트 할 최소한의 부분을 검색하고 Compute Diff함, 그 후 그 부분만을 업데이트하고 다시 렌더링
2. Component기반의 구조
- 레고 블록 조립하듯 컴포넌트들을 모아서 개발
3. 재사용성(Reusability)
- 다시 사용이 가능한 성질
- 다른 모듈에 의존성을 낮춰야 함
4. 든든한 지원군(Meta)
5. 활발한 지식공유 & 커뮤니티
- github, stackoverflow 등과 같은 활발한 커뮤니티
6. React Native를 통해 모바일 앱 개발 가능

단점

1. 방대한 학습량
- 기존과는 다른 UI방식이기 때문에 배워야 할 것이 많음
2. 높은 상태관리 복잡도

---

MPA

페이지가 1개 이상인 애플리케이션

SPA

single page application 페이지가 1개인 애플리케이션

페이지 수만큼 html파일이 존재하는 MPA but 리액트 프로젝트에서 html파일은 1개

SSR

Server Side Rendering

서버에서 페이지의 내용을 다 그려서 브라우저로 넘김

웹 사이트에 접속하면 서버에서 필요한 데이터를 모두 가져와 HTML파일을 만들고 만들어진 파일을 동적으로 제어할 수 있는 소스코드와 함께 클라이언트에게 보냄

CSR

Client Side Rendering

페이지의 내용을 브라우저에서 그림

즉 클라이언트에서 모두 처리

서버에서 전체 페이지를 한번 렌더링하여 보여주고 사용자가 요청할때마다 리소스를 서버에서 제공받아 클라이언트가 해석하고 렌더링함

렌더링이란?

서버로부터 요청해서 받은 내용을 브라우저 화면에 표시해주는 것

SSR과 CSR의 차이는 표시해줄 화면을 어디서 어떻게 그리냐의 차이