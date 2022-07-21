7/18일 학습내용 정리 - 은택

# 리액트 소개

리액트는 사용자와 웹사이트의 상호작용을 돕는 인터페이스 구축을 위한

자바스크립트의 UI 라이브러리로써

화면을 만들기위한 기능들을 모아놓은것

### 리액트의 장점

1.빠른 업데이트 & 렌더링 속도

업데이트 = 웹사이트 탐색시 화면이 바뀌는것

리액트는 이런 빠른 업데이트를 위해 내부적으로 Virtual Dom을 사용함

Virtual Dom은 말 그대로 가상의 돔을 의미하며 돔은 document object model의

약자로 웹페이지를 정의하는 하나의 객체이다

2.컴포넌트 기반의 구조

리액트에서는 모든 구성요소가 컴포넌트로 구성되어 있다.

재사용성이 좋음 →개발기간이 단축됨 + 유지보수가 용이

### 리액트의 단점

1.방대한 학습량

Virtual Dom, JSX, Component, State, Props등등의 새로운 개념들이 많음

버전 업데이트를 통해 계속해서 정보들이 추가되거나 바뀜 →새로 공부해야 함

2.높은 상태 관리 복잡도

state는 리액트 컴포넌트의 상태를 의미하는데 프로젝트의 규모가 커지면 상태 관리 규모도

커지게 되어 관리가 힘들다.

# 리액트 시작하기

### 웹사이트에 React.js 추가하기 -기존에있는 웹사이트에서 리액트적용

기존의 html파일에 돔 컨테이너를 추가해야 한다.

다음과 같이 root라는 아이디를 가진 div태그를 추가한다.

![화면 캡처 2022-07-18 200530.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d67b188e-e269-451a-a3a7-794e61b20828/화면_캡처_2022-07-18_200530.png)

이 div태그가 앞으로 돔 컨테이너로 사용될 예정이다.

다음으로 스크립트 태그를 통해 리액트에 자바스크립트 파일들을 가져올 수 있도록 한다.

![화면 캡처 2022-07-18 200641.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/069ec554-6f4d-4b93-8294-d89dba883184/화면_캡처_2022-07-18_200641.png)

다음은 리액트의 간단한 함수 컴포넌트이다.

### create-react-app →위와같이 복잡한 방법이 아니라 처음부터 리액트가 적용되어있는 상태로 개발하는 방법

# JSX

jsx는 자바스크립트의 확장 문법이다.

jsx = 자바스크립트 + XML / HTML

jsx예제코드

```jsx
const element = <h1>Hello, hi</h1>;
```

### 역할은?

jsx는 내부적으로 XML / HTML코드를 자바스크립트로 변환하는 과정을 가진다.

그래서

실제로 jsx코드를 작성해도 최종적으로 자바스크립트 코드가 나오게 됨.

jsx코드를 자바스크립트 코드로 변환하는 역할을 하는것이 리액트의.createElement라는 함수이다.

```jsx
class Hello extends React.Component{
    render( ) {
        return <div>Hello {this.props.toWhat}</div>;
    }

ReactDOM.render (
    <Hello toWhat="world" />
    document.getElementById('root')
)
```

위 코드를보면

헬로라는 이름을 가진 리액트 컴포넌트가 나오는데 컴포넌트 내부에서 jsx가 사용되고 있음.

그리고 이러한 컴포넌트를

리액트돔에 렌더함수를 사용해서 실제 화면에 렌더링하고있음.

### 장점

1.간결한 코드

jsx를 사용한 코드

```jsx
<div>Hello, {name} </div>
```

jsx를 안 사용한 코드

```jsx
React.createElement('div' , null , 'Hello , ${name}');
```

모두 동일한 결과값을 낸다.

2.가독성 향상

위 두 예제 코드를 보았을때 jsx를 사용한코드가 가독성이 더 좋음

→ 빨리 파악가능 + 버그 찾기 쉬움

3.injection Attacks 방어

위와 같은 해킹방법을 방어함으로써 보안성 향상

injection Attacks해킹은 입력창에 문자나 숫자와같은 일반적인 값이 아닌 소스코드를 입력하여

해당코드가 실행되도록하는 해킹방법

### JSX사용법

jsx는 js를 확장한 언어이기에 모든 js문법을 지원함

xml/html코드를 사용하다가 js코드를 사용하고 싶으면 { }로 묶어 사용하면된다.

(변수나 함수 넣을 수 있음)

태그의 속성에 값을 넣는 방법

```jsx
//큰따옴표 사이에 문자열을 넣거나
const element = <div tabIndex= "0"></div>;
//중괄호 사이에 자바스크립트 코드를 넣으면 됨
const element = <img src = {user.avatarUrl}></img>
```