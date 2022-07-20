# 3 (1)

## 리액트란 ?

- 사용자 인터페이스를 만들기 위한 자바스크립트 UI라이브러리다.
- 장점
    - 빠른 업데이트와 렌더링 속도
    - component 기반 → 재사용이 용이하다.
    - 활발한 지식 공유 & 커뮤니티 (github의 facebook/react 활용하기!)
    - react를 학습한 후, react native를 활용하여 모바일 웹도 개발이 가능해진다.
- 단점
    - 방대한 학습량..
    - 뭔가 자꾸 바뀐다..
    - 높은 상태관리 복잡도….?(쉽지 않다.)

## JSX란?

- JavaScript + XML .XML에 자바 스크립트를 추가한 확장 문법이다.
- 역할 : XML/HTML 코드를 자바스크립트 코드로 변환하는 역할을 한다. 하나의 파일에 자바 스크립트와 HTML을 동시에 작성할 수 있어 편리하다.
- 리액트에서 JSX를 사용하는 것이 필수는 아니다.
- 장점 : 코드가 간결해진다, 가독성이 높다, 버그를 발견하기가 쉽다.
- 사용 방법 : 자바스크립트와 XML/HTML을 섞어서 사용하면 된다.(?)
    - XML/HTML 코드를 사용하다가 자바스크립트 코드를 사용하고 싶으면, 중괄호로 묶은 뒤 중괄호 안에 자바스크립트 코드를 사용하면 된다.
        
        ```jsx
        const name = "세빈";
        const element = <h1>{name}이의 일기장</h1>;
        
        ReactDOM.render (
        	element,
        	document.getElementById('root')
        );
        ```
        
    - 태그의 속성에 값을 넣고 싶다면 아래 예시와 같은 방법을 사용한다.
        
        ```jsx
        const element = <div tabIndex="0"></div>;    //큰 따옴표 사이에 문자열 삽입
        const element = <img src={user.avatarUrl}></img>;  // 중괄호 사이에 자바스크립트 코드를 넣는다. 
        ```
        

## Elements

- 리액트 앱을 구성하는 가장 작은 블록들.

```jsx
React.createElement (  //객체 생성
	type,    // html 태그 이름이 문자열 또는 리액트 컴포넌트가 들어간다. 
	[props], // Element의 속성 (class, style ..)
	[...children]   // 자식 Element가 들어간다. 
)
```

- 기존 자바스크립트의 document.creatElement() 함수를 사용하여 객체 모델을 생성하는 것이다.
- element는 한 번 생성된 후, 수정이 불가하다.