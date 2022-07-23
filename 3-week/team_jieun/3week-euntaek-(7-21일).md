7월 21일 학습내용 - euntaek


# Rendering Elements

### elements의 정의

elements는 리액트앱를 구성하는 가장 작은 블록들(요소)을 의미

원래 웹사이트에 대한 모든정보를 담고있는 객체인 돔에서 사용하는 용어였음.

그래서 elements는 돔 elements를 의미했음

리액트 elements와 돔elements의 차이점은?

실제 브라우저의 돔에 존재하는 elements는 돔 elements이고,

리액트의 virtual돔에 존재하는 elements가 리액트 elements이다.

리액트 elements는 돔elements의 가상표현이다.

그리고 돔 elements는 리액트 elements에 비해서 많은정보를 담고있기때문에

상대적으로 크고 무겁다.

리액트 elements는 화면에 보이는것을 기술하고 elements가 기술한 내용을 토대로

실제 화면에서 보는 돔 elements가 만들어짐

```jsx
const element = <h1>hello ? </h1>;
```

위 코드가 실행될때 오른쪽 부분은 리액트의 create elements함수를 사용하여 elements를

생성하게됨 → 이렇게 생성된것이 리액트 elements

그리고 리액트가 이 elements를 사용하여 화면에서 보는 돔 elements를 생성함

### elements의 생김새

리액트 elements는 js의 객체 형태로 존재함

버튼을 나타내기위한 elements

```jsx
{
		type: 'button' ,
		props: {
				className: 'bg-green' .
						type: 'b' ,
						props: {
								children: 'hello, hi'
					  }
				}
		}
}
```

자바스크립트의 객체형태임

이렇게 타입에 html의 태그이름이 문자열로 들어가는 경우 elements는 해당태그이름을 가진

 돔 노드를 나타내고 props는 속성에 해당.

위 elements가 렌더링이 되면?

```jsx
<button class='bg-green'>
    <b>
        hello, hi
    <b>
</button>
```

이렇게 돔 elements가 됨.

리액트 elements는 자바스크립트의 객체형태로 존재

이 객체를 만드는 역할? → create elements함수

### 리액트 엘리먼트의 특징

불변성

한번생성된 엘리먼트는 변하지 않음 → 엘리먼트 생성후 children, attributes 변경 불가능

### 렌더링

엘리먼트 생성후 화면에 나오게 하기위해 렌더링이라는 과정을 거침

방법은?

```jsx
<dlv id="root"></div>
```

위 코드는 모든 리액트앱에 필수적으로 포함된다. 

이 div태그안에서 리액트 엘리멘트들이 렌더링되며 이것을 rootdom노드라고 부른다

div태그안에 모든것이 리액트돔에 의해 관리된다.

```jsx
const element = <h1> hi? </h1>;
ReactDom.render(element, document.getElementById('root'));
```

위 코드는 첫번재 줄에서 엘리먼트를 생성하고 생성된 엘리먼트를  root div에 렌더링하는 코드임

렌더링을 위해 리액트돔의 렌더함수를 사용함.

리액트 엘리먼트가 렌더링되는 과정은 버츄얼돔에서 실제돔으로 이동하는 과정

# Components ans Props

### 리액트의 Components

리액트에서 모든 페이지는 컴포넌트로 구성되어 있으며 하나의 컴포넌트는 또 다른 여러개의

컴포넌트의 조합으로 구성되었다. 그리고 이러한 컴포넌트들을 또 조합하여 새로운 컴포넌트를

만들어 낼 수 있음.

### 리액트 컴포넌트는 개념적으로 자바스크립트에 함수와 비슷하다?

js에서 함수가 입력에 따른 출력을 하는것과 같이

리액트 컴포넌트도 입력을 받고 그에 맞는 출력을 한다.

그러나 개념적으로 비슷할뿐 js와 조금 다르다.

리액트 컴포넌트에서의 입력은 Props라는 것이고

출력은 리액트 엘리먼트가 된다.

→ 어떠한 속성들을 입력받고 그에 따른 리액트 엘리먼트를 생성하여 반환

### 리액트의 Props

Property  = → 속성

### Props의 특징

1.Read-Only → 읽기 전용

리액트 엘리먼트의 특징이 불변성 → Props는 리액트컴포넌트가 엘리먼트를 생성하기위해 사용하는

값이다.  이 값이 엘리먼트 생성도중 변한다면 제대로된 엘리먼트 생성불가

다른 Props의 값으로 엘리먼트를 생성하고싶으면?

→ 새로운값을 컴포넌트에 전달하여 새로운 엘리먼트를 생성하면됨

이과정에서 엘리먼트가 다시 렌더링됨.

### Props사용법

jsx의 경우

```jsx
function Hello(props){
		return (
				<Profile
						name = "은택"
						introduction = "22학번 응소입니다."
						account = {250,000}
				/>
    );
}
						
```

key와 value값으로 이루어진 키, 값의 형태로 props를 사용할수있음.

? value값중 “”와 {}의 차이는 무엇일까?

jsx코드에서 {}안에는 js코드가 들어감 문자열 이외의 정수,변수, 다른 컴포넌트를 넣을때

줄괄호로 감싸야됨.

후에

profile 컴포넌트로 Props가 이동하고

```jsx
{
		name = "은택"
		introduction = "22학번 응소입니다."
		account = {250,000}
}
```

Props는 이와같이 js의 객체가 됨.

Props에 중괄호를 사용해서 아래와같은 컴포넌트도 넣을 수 있음.

```jsx
header={
    <Header title="hi" />
}
```

jsx를 사용하지 않는경우에는 어떻게 Props를 추가할까?

→리액트의 createElement함수를 통해서 추가한다.

```jsx
React.createElement(
		type,
		[Props],
    [...children]
)

```

위의 코드가 createElement함수는 다음과 같은 형태로 사용

이때 Props에 자바스크립트 객체를 추가하면 그게 해당 컴포넌트의 props가됨

### Component만들기

리액트 컴포넌트는 함수 컴포넌트와 클래스 컴포넌트로 나뉜다.

### 함수 컴포넌트

```jsx
function Welcome(props) {
		return <h1> hi , {props.name}</hi>;
}
```

코드는 하나의 props를 받아 리액트 엘리먼트들을 반환하기에 리액트 컴포넌트라 할 수 있다.

그리고 이러한 함수형 컴포넌트를 함수 컴포넌트라 부른다.

### 클래스 컴포넌트

함수 컴포넌트에 비해 추가적 기능을 가지고 있다.

```jsx
class Welcome extends React.Component {
    render() {
		    return <h1> hi , {this.props.name}</hi>;
    }
}
```

리액트의 모든 클래스컴포넌트는 React.Component를 상속받아 만들어야됨

### 컴포넌트 이름 짓는 방법?

Component의 이름은 항상 대문자로 시작해야함.

→ 소문자는 돔 태그로 인식함

컴포넌트는 대문자로

```jsx
const element = <Welcome name = "hi" />;
```

→대분자는 리액트 컴포넌트로 인식

### 컴포넌트 합성

여러개의 컴포넌트를 합쳐 하나의 컴포넌트로 만드는것

리액트는 컴포넌트안에 또 다른 컴포넌트를 사용가능

→ 복잡한 화면을 여러개의 컴포넌트로 나눠 구현

```jsx
function Welcome(props) {
		return <h1> hi , {props.name}</hi>;
}

function Wow(props) {
		return (
        <div>
            <Welcome name ="은택1" />
            <Welcome name ="은택12" />
            <Welcome name ="은택123" />
        </div>
    )
}
```

### 컴포넌트 추출

재사용성 향상 + 개발속도 향상

```jsx
function Comment(Props) {
    return (
				<div className = "comment">
						<div className = "user-info"
								<img className = "avatar"
										src = {props.author.avatarUrl}
										alt = {props.author.name}
								/>
								<div className= "user-info-name">
										{props.author.name}
								</div>
						<div className = "comment-text">
								{props.text}
            </div>
				</div>
		);
}
```

1.avatar 추출

```jsx
function Avatar(props) {
		return (
				<img className = "avatar"
						src={props.user.avatarUrl}
						alt={props.user.name}
		    />
		);
}

```

```jsx
<img className = "avatar"
			src = {props.author.avatarUrl}     ->   <Avatar user={props.author} />
			alt = {props.author.name}
/>
```

가독성이 향상됨.