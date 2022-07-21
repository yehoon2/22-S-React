7/22일 학습내용 정리 euntaek

# State와 Lifecycle

## State

state는 상태라는 의미를 가지고 있다.

리액트에서 state는 리액트 컴포넌트의 상태를 의미한다.

이때 ‘상태’의 의미는 정상/비정상의 문제를 따지는것이 아니라

리액터 컴포넌트의 데이터를 말한다.

State → 리액트 컴포넌트의 변경 가능한 데이터 + js 객체이다

*state는 리액트 컴포넌트를 개발하는 개발자가 정의하는것임.

이때 state값으로 렌더링이나 데이터 흐름에 사용되는 값만 포함시켜야한다.

→state가 변경되면 컴포넌트가 다시 렌더링 되기에 렌더링과 데이터흐름에 관련없는 값을

포함하면 불필요한 렌더링이 생겨 성능 저하로 이어진다.

다음은 LikeButton 이라는 리액트 클래스 컴포넌트이다.

```jsx
class LikeButton extends React.Component {
    constructor(props) {
				super(props);

				this.state = {
						liked: false
				};
		}

		...
}
```

모든 클래스컴포넌트에는 constructor이라는 함수가 존재한다.(생성자라는 의미이다.)

→ 클래스가 생성될때 실행됨

이때 아래의 코드가

this.state = {
	liked: false
};

현재컴포넌트의 state를 정의하는 부분

클래스컴포넌트의 경우 state를 생성자에서 정의한다. → 이후 마음대로 수정 할 수 없다.

클래스컴포넌트에서 state를 변경하려면 setState함수를 사용해야한다.

```jsx
this.setState = {
		liked: false
};
```

# Lifecycle

→ 생명주기

리액트 컴포넌트는 생명주기를 가진다.

리액트 컴포넌트는 생성되는 시점과 사라지는 시점이 있다.

### 리액트 컴포넌트 생명주기

아래의 그림은 리액트 컴포넌트의 생명주기를 나타낸 그림이다.

출생 - 인생 - 사망 순이며

초록색 부분은 생명주기에 따라 호출되는 클래스컴포넌트의 함수이다. → 생명주기함수

![Lifecycle.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5f02df57-d352-4cc2-a951-ee12ebc86114/Lifecycle.png)

컴포넌트가 생성되는 시점의 과정을 mount라 부르며 이때 컴포넌트의 생성자가 실행된다.

이후 렌더링되고 아래 생명주기함수가 호출된다.

리액트 컴포넌트가 변화를 겪고 여러번 렌더링 되는 과정을 update라고 부른다

→ Props변경 or setState함수를 통해 state가 변경되거나 강제 렌더링 함수를 통해 렌더링되는

경우

이후 아래 생명주기함수가 호출된다.

리액트 컴포넌트가 종료되는 순간을 unmount라고 한다.

—> 상위컴포넌트에서 현재 컴포넌트를 더 이상 화면에 표시하지 않을때 unmount됨

이후 아래 생명주기함수가 호출된다.

### Lifecycle의 핵심

→컴포넌트가 계속 존재하는 것이 아니라

시간의 흐름에 따라 생성되고 업데이트되고 또 사라진다.