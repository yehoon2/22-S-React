# 3 (2)

## Component에 들어가기에 앞서 웹 프레임워크의 작동 원리

- 기존의 웹 프레임워크는 MVC 방식을 활용했다.
    - **MVC**란 ? 정보를 담당하는 모델(**M**odel), 화면을 담당하는 뷰(**V**eiw), 구동을 담당하는 컨트롤러(**C**ontroller)을 뜻한다.
- MVC방식은 코드 관리를 효율적으로 할 수 있다는 장점이 있으나 각 요소의 의존성이 높아 재활용이 어렵다는 단점이 존재한다. (하나의 요소만을 바꾸기가 쉽지 않다.)
- 하지만, 우리가 보는 웹 사이트들의 화면은 각 요소가 비슷하고 반복적으로 사용이 된다는 것을 알 수 있다.
- 그렇다면 의존성도 낮고 코드를 효율적으로 관리 할 수 있는 것이 없을까 ? 해서 등장한 것이 component라고 한다.
    - MVC의 뷰를 독립적으로 구성하며 재사용도 할 수 있게 되었다.
    - component를 통해 새로운 컴포넌트를 쉽게 만들 수 있게 되었다.

## Component

- 작은 component들이 모여서 하나의 component를 구성하고 이러한 component들이 모여서 하나의 페이지가 생성된다.
- props를 통해 입력을 받고 React element를 통해 출력한다.
- Function Component
    - 일종의 함수라고 생각하면 편하다.
    - 사용하기 간단하다는 장점이 존재한다. 아래 코드는 함수 component의 예시이다. (순수함수 형태로 작성된 것을 볼 수 있다. )
        
        ```jsx
        function Welcome(props){
        	return <h1>안녕, {props.name}</h1>;
        }
        ```
        
- Class Component ( 불편하다는 의견이 많아 잘 사용하지 않는다. )
    - 리액트의 모든 class component는 React.Component를 상속 받는다.
        
        ```jsx
        class Welcome extends React.Component {
        	render() {
        		return <h1>안녕, {this.props.name}</h1>;
        }
        ```
        
- 주의 사항
    - Component의 이름은 항상 대문자로 시작해야 한다. (리액트는 소문자로 시작하는 태그를 DOM 태그로 인식하기 때문이다. )
        - 왼쪽 예시는 리액트가 element를 HTML div로 인식하고, 오른쪽 예시는 리액트가 Welecome이라는 리액트의 component로 인식한다.
        
        ```jsx
        const element = <div />;
        ```
        
        ```jsx
        const element = <Welcome name ="세빈" />;
        //welcome과 같이 소문자로 시작할 경우 리액트는
        //이것을 dom 태그로 인식한다. 
        ```
        

## Props(property)

- 리액트 component의 속성을 의미한다.
- 컴포넌트에 전달할 다양한 정보를 담고 있는 자바스크립트 객체라고 생각하면 된다.
- 특징
    - 상위 컴포넌트가 하위 컴포넌트에 값을 전달할 때 사용한다.  (단방향으로 데이터가 흐른다. ) (인프런 예제중 Library , book 을 예시로 들면 데이터가 library에서 book으로 흐른다고 볼 수 있다. (???))
    - 읽기전용이다. 그렇기 때문에 값을 변경할 수 없다. ( + 변경을 하고 싶다면, 새로운 값을 컴포넌트에 전달하여 새로 Element를 만들어야 한다.)
    - 모든 React 컴포넌트는 자신의 props를 다룰 때 반두시 순수 함수처럼 작동되게 만들어야 한다.  (오류가 생겼을 때 전체를 점검할 필요없이 해당 순수 함수만 보면 되기 때문에 사용한다.)
        - 순수함수란, 입력값을 변경하지 않으며, 같은 입력값에 대해서는 항상 같은 출력 값을 리턴 받는 함수이다.
    
    ```jsx
    function sum (a,b){
    	return a+b;
    }  // 순수함수의 예시이다.
    ```
    
    ```jsx
    function withdraw(account, amount){
    	account.total -=amount;
    }    // 순수함수가 아닌 함수의 예시이다.
    ```
    
- props 사용법
    - 키와 값 형태
        
        ```jsx
        function App(porps){
        	return (
        		<Profile
        			name="세빈"
        			introduction="안녕하세요! 융소 21학번 김세빈입니다."
        			/>
        	);
        }
        ```
        
    - props에 중괄호를 사용하여 props의 값으로 component를 넣을 수 있다.
        
        ```jsx
        function App(porps){
        	return (
        		<Layout     
        			width={2560}      // 숫자나 boolean 값들은 중괄호를 사용한다. 
        			height={1440}     // height="1440"  문자열로 인식
        			header= {
        				<Header titile="세빈이의 블로그입니다." />
        			}
        		footer={
        			<Footer />			
        		}
        	);
        }
        ```
        
    - 주의 사항.
        - 프로퍼티에 문자열을 전달할 때는 큰 따옴표””를 사용한다. 하지만 , 숫자형이나 boolean 등의 값을 전달할 때는 큰따옴표를 사용할 수 없다. numbers=”0129”등과 같은 방법으로 프로퍼티에 전달하면 문자열로 인식하기 때문이다. 그렇기 때문에 리액트에서 문자열 외의 값은 따옴표대신 중괄호{}를 사용한다.

## props(property) 자료형 선언

- 객체 구조 분해 할당을 하기 전, 먼저 프로퍼티의 자료형을 미리 선언해주는 것이 좋다.
    - 미리 선언할 경우 리액트 엔진이 프로퍼티로 전달하는 값의 변화를 효율적으로 감지할 수 있다.
    - 개발자가 실수로 지정되지 않은 자료형을 프로퍼티에 전달하려고 할 때 경고 메시지로 알려주기 때문에 버그를 예방할 수 있다.
- 프로퍼티 자료형 선언 방법
    - import PropTypes from ‘prop-types’; 를 사용해 ‘prop-types’ 라이브러리를  PropTypes 이름으로 import한다.
    - Component이름.propTypes = { name : PropTypes.string,}; 과 같이 프로퍼티의 자료형을 객체형태로 지정하여 Component이름.propTypes에 저장하였다.
    - 위에서 지정되지 않은 자료형을 프로퍼티에 전달하려고 할 때 경고메시지가 뜬다고 했는데, 이 경우에 name :20 등 string이 아닌 값이 들어가면 경고 메시지가 뜬다.

```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PropsComponent extends React.Component {
	render() {
		return (
			<div>
				{this.props.name}
			</div>
			);
		}
}
//자료형 선언
PropsComponent.propTypes={
	name : PropTypes.string,
};

export dafault PropsComponent;
```

```jsx
import React from 'react';
import PropsComponent from './03/PropsComponent';

class App exrends React.Component {
	render() {
		return {
			<PropComponent
				name ="세빈이의 리액트 스터디"    //name : 20 경고메시지가 뜬다.
			/>
		);
	}
}
export default App;
```

## 객체 구조 분해 할당

- 객체 구조 분해 할당식을 사용할 경우 프로퍼티에 전달된 값들이 함수 내에서 지역변수로 재정의 한다.
- 객체 구조 분해 할당식을 사용하면 this.props를 제외할 수 있다. 그렇기 때문에 프로퍼티에 간단하게 접근이 가능하다.
- 프로퍼티 목록의 역할을 하기 때문에 개발을 할 때 참고하기도 좋다고 한다 !

```jsx
//객체 구조 분해 할당을 하기 전, 자료형 선언을 먼저 해준다.
import React from 'react';
import PropTypes from 'prop-types';

class SebinComponent extends React.Component {
	render()
		const {
		boolValue,
		numValue,
		arrayValue,
		nodeValue,
		objValue,
		funcValue,
	} = this.props;

	return (
		<div>
			<span>불리언 값: {boolValue}</span>
			...
			<span>객체 값: {String(objValue)}</span>
			<span>함수 값: {String(funcValue)}</span>
		);
	}
}
SebinComponent.propTypes = {
	boolValue : PropTypes.bool,
	numValue : PropTypes.number,
	arrayValue : PropTypes.arrayOf(PropTypes.number),
...
}
export dafault SebinComponent;
```

```jsx
import React from 'react';
import SebinComponent from './03/SebinComponent';

class App extends React.Component {
	render() {
		const array = [1, 29];     
		const obj = {univ : "명지대학교", id: 21};
		const node = <h1>안녕하세요</h1>;.
		const func = () => {console.log('메시지');};
		return (
			<SebinConponent 
				boolValue = {true}
				numValue = {20220721}
				arrayValue = {array}   //변수에 객체를 담아서 전달도 가능하다. 
				objValue = {obj}
				nodeValue = {node}
				funcValue = {func}
			/>
		);
	}
}
export default App;
```