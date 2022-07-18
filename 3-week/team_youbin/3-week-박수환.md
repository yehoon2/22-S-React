### React

자바스크립트 UI라이브러리

### React 장단점

장점

- 빠른 업데이트와 렌더링 속도 - Virtual DOM 사용
- Component-Based(웹사이트를 컴포넌트들의 조합으로 만듬)
- 재사용성

단점

- 방대한 학습량
- 높은 상태관리 복잡도

### JSX

자바스크립트의 문법을 확장

JavaScript + XML/HTML

내부적으로 작성된 XML/HTML코드가 자바스크립트 코드로 변환된다. → React.createElement가 수행

JSX 장점

- 코드가 간결해진다.
- 가독성 향상
- Injection Attacks 방어 - 보안성 향상

### SPA vs MPA

SPA(Single Page Application)

- 한개의 페이지로 구성된 Application이다.
- 웹 애플리케이션에 필요한 정적 리소스를 최초에 한번 다운로드 후 새로운 페이지 요청에 따라 필요한 데이터만 전달 받아 페이지를 갱신한다.

MPA(Multiple Page Application)

- 여러 개의 페이지로 구성된 Application이다.
- 새로운 페이지를 요청할 때마다 정적 리소스를 다운로드하고 매번 전체 페이지가 다시 렌더링 된다.

