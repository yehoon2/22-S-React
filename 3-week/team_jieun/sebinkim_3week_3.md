# 3 (3)

## State

- 리액트 컴포넌트의 상태를 의미한다. (리액트의 컴포넌트의 변경가능한 데이터)
- 쇼핑몰에서 물건 수량을 입력하거나, 상품에 댓글을 남기는 등 상태를 바꿔야하는 경우 사용한다. (+ 버튼을 클릭하거나 값을 입력하는 등의 이벤트와 함께 사용된다! )
- 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야 한다.
- 주의 사항
    - 생성자 (constructor)에서 반드시 초기화 해야 한다.
    
    ```jsx
    import React from 'react';
    
    class SebinExample extends React.Component {
    	constructor(porps) {  // 맨 처음 생성될 때 한 번만 호출.
    		super(props);       
    		this.state = {
    			name: 'subin',
    		};
    	}
    	...
    }
    ```
    
    - state를 직접 수정할 수 없다.  setState() 함수를 활용하여 수정한다.
    
    ```jsx
    this.state = {
    	name: 'sebin'
    };    //잘못된 수정 방법이다.
    ```
    
    ```jsx
    this.setState = ({
    	name: 'sebin'
    });   // 올바른 수정 방법이다. 
    ```
    
    - setState() 함수는 비동기로 처리되며, setState() 코드 이후로 연결된 함수들의 실행이 완료된 시점에 화면 동기화 과정을 거친다.

## Lifecycle

- component의 생성부터 소멸까지의 과정을 component의 생명주기(lifecycle)이라고 부른다.
- 생명주기 함수를 사용하면 특정 시점에 원하는 동작을 하도록 만들 수 있다.
- constructor를 통해 클래스 컴포넌트를 생성을 하고, render를 통해 작동을 하다가 더 이상 화면에 표시하지 않게 될 때 소멸한다.
- 요점은, component가 계속 존재하는 것이 아니라 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다는 것이다.
- 생성 과정의 생명 주기 함수
    - constructor : 최초 생성주기 함수이다.  state를 선언할 때 사용한다. 함수를 정의할 때 항상 super() 함수를 가장 위에 호출해야한다. (+ super()은 프로퍼티와 생명 주기 상태 등을 초기화 하는 중요한 과정을 포함하고 있다. )
    - state getDerivedStateFromProps : 정적함수이기 때문에 state나 프로퍼티에 접근 불가. 상위 컴포넌트에서 전달받은 프로퍼티로 state값을 연동할 때 사용한다. 반환 값으로 state를 변경한다.
    - render() : render()함수가 반환하는 JSX를 화면에 출력해준다.
- 변경 과정의 생명 주기 함수
    - componentDidMount : render()함수가 jsx를 화면에 그린 이후 호출되는 함수이다. 컴포넌트가 화면에 모두 표현된 후 해야하는 작업들은 이 함수를 통해서 하면된다.
    - shouldComponentUpdate : 화면을 새로 출력할지 말지 판단하는 함수이다. 데이터 변화를 비교하는 작업을 포함하기 때문에 리액트 성능에 영향을 많이 준다.
    - getSnapshotBeforeUpdate : 컴포넌트의 변경된 내용이 가상화면에 완성된 이후 호출되는 함수이다. 컴포넌트가 실제로 출력되기 전에 호출되며 DOM 정보에 접근할 때 사용된다.
    - componentDidUpdate : 컴포넌트가 실제 화면에 출력된 이후 호출된다. 부모 컴포넌트로부터 전달된 이전 프로퍼티+ 이전 state + getSnapshotBeforeUpdate()함수에서 반환된 값을 인자로 받는다. 이 값들을 사용하여 DOM 정보를 변경할 수 있다.
- 소멸 과정의 생명 주기 함수
    - componentWillUnmount : 컴포넌트가 소멸되기 직전에 호출되는 함수이다.컴포넌트에서 감시하고 있는 작업들을 해제할 때 필요한 함수이다. (ex. setInterval 함수가 사용되면 clearInterval 함수를 통해 해제해야 하는데 그때 사용된다.)