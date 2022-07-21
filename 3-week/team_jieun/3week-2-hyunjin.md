# <Components and Props>

- Component
- 리액트 : component 기반
- 레고 블록을 조립하듯이 조립해서 component들을 반복적으로 사용해 전체 코드의 양을 줄이며 하나의 페이지를 구성
- js의 함수와 비슷함! (입력과 출력은 다름)

- Props
- component에 전달할 다양한 정보를 담고 있는 js 객체
- 입력: Props, 출력: React element(react app을 구성하는 가장 작은 빌딩 블럭들, js 객체 형태로 존재, 화면에 보이는 것을 기술)
- component: 붕어빵 틀, element: 붕어빵, props: 붕어빵에 들어가는 재료!(팥, 슈크림 …)
- props: 같은 react component에서 눈에 보이는 속성을 바꾸고싶을 때 사용하는 것이라고 생각하면 됨
- Props 특징
- 읽기 전용 = 값을 변경할 수 없다

- ‘Pure’하다 : 입력값을 변경하지 않으며, 같은 입력값에 대해서는 항상 같은 출력값을 리턴함
    
    ```jsx
    function sum(a,b){
    	return a+b;
    }
    ```
    
     - ’Impure’하다: 입력값을 변경
    
    ```jsx
    function withdraw(account, amount){
    	account.total -= amount;
    }
    ```
    
    - 모든 리액트 컴포넌트는 Props를 직접 바꿀 수 없고, 같은 Props에 대해서는 항상 같은 결과를 보여줄 것!
    
- Props 사용법

```jsx
function App(props){
	return(
		<Profile
			name='현진'
			introduction='안녕하세요, 현진입니다.'
			viewcount={1500}
		/>
	);
}
```

-jsx 사용하는 경우: 키, 값의 형태로 props를 넣을 수 있음

- 리액트 component 종류

 - 함수 컴포넌트

```jsx
 function Welcome(props){
	return <h1>안녕, {props.name}</h1>;
}
```

 - 클래스 컴포넌트

```jsx
class Welcome extends React.Component{
	render(){
		return <h1>안녕, {this.props.name}</h1>;
	}
}
```

 - 리액트의 모든 클래스 컴포넌트는 React.Component를 상속받음

<aside>
💡 컴포넌트의 이름은 항상 대문자로 시작해야 한다!
 - 리액트는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문

</aside>

- 컴포넌트 렌더링

```jsx
function Welcome(props){
	return <h1>안녕, {props.name}</h1>;
}

const element = <Welcome name="현진" />;
ReactDOM.render(
	element,
	document.getElementById('root')
);
```

- 컴포넌트 합성: 여러 개의 컴포넌트를 합쳐 또 다른 컴포넌트를 만드는 것

```jsx
function Welcome(props){
	return <h1> hello, {props.name}</h1>;
}

function App(props){
	return (
		<div>
			<Welcome name="지은" />
			<Welcome name="혜정" />
			<Welcome name="주현" />
		</div>
	)
}

ReactDOM.render(
	<App />,
	document.getElementById('root')
);
```

 → App 컴포넌트 안에 3개의 Welcome 컴포넌트가 있고, 각각의 Welcome 컴포넌트는 각기 다른 Props를 가지고 있다.

- 컴포넌트 추출: 복잡한 컴포넌트를 여러 개의 새로운 컴포넌트로 나누는 것

 - 컴포넌트의 재사용성이 올라감 → 컴포넌트가 작아질 수록 해당 컴포넌트의 기능과 목적이 명확해지고, props도 단순해짐

 - 개발속도가 올라감

<aside>
💡 어느정도 수준까지 추출하는가? 정해진 기준은 없음.
But 기능 단위로 구분하는 것이 좋고, 나중에 곧바로 재사용이 가능한 형태로 추출하는 것이 좋다.

</aside>

- 재사용이 가능한 컴포넌트를 많이 가지고 있을수록, 개발 속도가 빠르다.