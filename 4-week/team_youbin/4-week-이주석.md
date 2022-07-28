## 리액트 (React)

### Component
    • 컴포넌트를 통해 UI를 재사용 가능한 개별적인 여러 조각으로 나눈다.
    • 컴포넌트는 개념적으로 JavaScript 함수와 유사하다. 'props'라는 입력을 받은 후, 화면에 어떻게 표시되는지 기술하는 React 엘리먼트를 반환한다.
    • 엘리먼트는 일반 객체(plain object)로 React 앱의 가장 작은 단위다. 엘리먼트는 컴포넌트의 '구성 요소'다.
    • 컴포넌트를 선언하는 방식에는 함수형 컴포넌트와 클래스형 컴포넌트가 있다.

🌱 Function Component
```js
function Welcome(props) {
    return <h1>안녕, {props.name}</h1>;
}
```
    • 함수형 컴포넌트는, props로 받을 객체 인자를 정의하고, JSX를 반환하는 것으로 기본 형태를 갖춘다.
    • 함수형 컴포넌트에서는 return문에서 JSX를 반환할 수 있다.

🌱 Class Component
```js
class Welcome extends React.Component {
    render() {
        return <h1>안녕, {this.props.name}</h1>;
    }
}
```
    • 클래스형 컴포넌트는 React.Component 클래스를 상속(이미 구현되어 있는 클래스에 기능을 추가함)받는 것으로 기본 형태를 갖춘다.
    • 컴포넌트는 jsx를 반환해야하는데, 클래스는 return 문을 사용할 수 없으므로, 클래스형 컴포넌트에서는 JSX를 반환하기 위해 render() 함수를 사용한다. 리액트는 클래스형 컴포넌트의 render() 함수를 자동으로 실행시킨다.

### props
    • 컴포넌트는, 데이터를 가진 하나의 'props' 객체 인자를 받은 후 React 엘리먼트를 반환한다. 이때 props는 속성을 나타내는 데이터다.
    • props는 컴포넌트에서 컴포넌트로 전달하는 데이터다. 컴포넌트의 속성으로, 해당 컴포넌트를 불러와 사용하는 부모 컴포넌트에서만 설정 가능하다.

🌱 props 지정하기
    • props는 <ComponentName prop1={propValue1} prop2={propValue2} ... /> 형태로 컴포넌트를 부를 때 함께 지정한다.
    • 같은 타입의 컴포넌트에 다른 props 값을 주어, 패턴이 반복되는 형태로 컴포넌트의 효율적인 재사용이 가능하다.
    • props에는 불리언 값(true, false), 숫자, 배열과 같은 다양한 형태의 데이터를 담을 수 있다. 공백 구분으로 여러 개를 담는 것도 가능하다.
        💡 props에 있는 데이터는 문자열인 경우를 제외하면 모두 중괄호({})로 값을 감싸야 한다.

🌱 props 받아 사용하기
    • 💡 props는 읽기 전용이므로 컴포넌트의 내부에서 props를 수정해서는 안 된다. 
      입력값을 수정하지 않는 함수를 순수 함수라고 호칭하며, 모든 React 컴포넌트는 자신의 props를 다룰 때, 순수 함수처럼 동작해야한다.
    • props를 받을 때, 구조 분해 할당을 사용하여 점 연산자 사용을 줄일 수 있다.
    • 클래스형 컴포넌트에서 props를 사용할 때는 this.props로 불러와 사용한다. 
      클래스형 컴포넌트에서 propTypes나 defaultProps를 사용할 때는, 클래스 내부에서도 지정할 수 있다.

### state
    • state는 컴포넌트 내부의 동적 데이터를 의미한다. props는 부모 컴포넌트가 설정하는 값으로 컴포넌트 자신은 props를 읽기 전용으로만 사용할 수 있다.

    • state를 사용하는 방식에는 컴포넌트의 종류에 따라 2가지가 있다. 
      클래스형 컴포넌트에서는 컴포넌트 자체가 state를 지니는 방식으로 사용한다.
      함수형 컴포넌트에서는 useState라는 함수, Hook을 통해 사용한다.

    • 여러 개의 자식으로부터 데이터를 모으거나 두 개의 자식 컴포넌트들이 서로 통신하게 하기 위해서 조상 컴포넌트에 state를 정의한다. 
      조상 컴포넌트가 props를 사용하여 자식 컴포넌트에 state를 다시 전달함으로 서로 동기화한다.
      두 컴포넌트 간 state 값을 동기화하는 일, state를 공유하는 일은, 그 state 값을 필요로 하는 컴포넌트 간의 가장 가까운 공통 조상 컴포넌트로 state를 끌어올림으로 가능하다. 
        👉 여러 개의 컴포넌트 간의 state를 동기화시키기보다, 공통 조상으로 끌어올려 하향식 데이터 흐름을 이용하자.

### Hooks

📌 Hook의 규칙
    1. 최상위에서만 Hook을 호출
        • React 함수(컴포넌트)의 최상위에서만 Hook을 호출 할 것.
        • 반복문, 조건문, 중첩된 함수등에서 호출 X

    2. React 함수에서만 Hook을 호출
        • Custom Hook에서는 호출 가능
        • 일반적인 Javascript 함수에서는 호출 X

    3. Hook을 만들때 앞에 use 붙히기
        • 그래야만 한눈에 보아도 Hook 규칙이 적용되는지를 파악할 수 있기 때문

    4. React는 Hook 호출되는 순서에 의존
        • 한 컴포넌트에서 여러개의 hook이 사용되는 경우
        • hook은 위에서부터 아래로 순서에 맞게 동작한다.

📌 Hook의 장점
    기본적으로 클래스형 컴포넌트보다 쉽고 직관적으로 같은 기능을 만들 수 있다.

    1. 함수형 컴포넌트로 코드 통일 가능
        • 이전에는 state유무로 있으면 클래스형 / 없으면 함수형으로 분리해서 작업했다고 함

    2. useEffect로 클래스형 Lifecycle에 흩어져 있는 로직 묶음
        • hook은 Lifecycle과 달리 여러번 선언가능 해 코드가 무엇을 하는지에 따라 hook별로 분기가 가능하다.

    3. Custom Hook을 이용해 손쉽게 로직 재사용 가능함
        • 클래스형 컴포넌트에서 로직을 재사용하기 위해 썼던 HOC나 render-props 같은 패턴이 가져오는 컴포넌트 트리의 불필요한 중첩을 없애줌

📌 Hook의 종류
    기본 Hooks
    🌱 useState (동적 상태 관리)
```js
    const [state, setState] = useState(initialState);

    // params : state의 기본값, 초기값.
    // return : [상태 값, 상태 설정 함수] 형태의 배열
```
    • setState(newState);
        상태 설정 함수 setState 함수는 state를 갱신할 때 사용한다.
        새 state값을 받아 컴포넌트 리렌더링을 큐에 등록하고, 다음 리렌더링 시 useState에서
        반환 받은 state 상태 값은 갱신된 최신 state 값을 가진다.

    • 하나의 useState는 하나의 state만 관리할 수 있다. 컴포넌트에서 관리할 상태가 여러 개라면 useState를 여러 번 사용할 수 있다.

    🌱 useEffect (side effect 수행 -mount/unmount/update)
```js
    useEffect(function, [...]);

    // params : 1.어떤 effect를 발생하는 함수  2.(조건부 effect) effect가 종속되어 있는 값의 배열
    // return(정리 effect) : 정리(clean-up) 함수
```
    • 기본 동작은 모든 렌더링을 완료한 후 effect를 발생하는 것으로, 의존성 중 하나가 변경된다면 effect는 항상 재생성된다.
    • 특정 값 업데이트 시에만 실행되는 조건부 effect에서는, 두번째 인자로 종속값 배열을 준다.
      마운트될 때만 실행하고 싶은 경우, 두번째 인자로 빈 배열을 넣어준다.
    • 컴포넌트 언마운트 전 혹은 업데이트 전 정리(clean-up)가 필요한 effect에서는, return에 정리(clean-up) 함수를 반환한다.

    🌱 useContext (컴포넌트를 중첩하지 않고도 전역 값 쉽게 정리)

    추가 Hooks
        🌱 useReducer (복잡한 컴포넌트들의 state를 관리 -분리)
        🌱 useCallback (특정 함수 재사용)
        🌱 useMemo (연산한 값 재사용)
        🌱 useRef (DOM선택, 컴포넌트 안에서 조회/수정할 수 있는 변수 관리)

### Handling Events
    🌱 클래스형 컴포넌트
        React에서는 DOM엘리먼트가 생성된 후 리스너를 추가하기 위해 addEventListener를 호출할 필요가 없다.
        대신, 엘리먼트가 처음 렌더링될때 리스너를 제공하면 된다.

    🌱 함수형 컴포넌트
        일단 함수형 컴포넌트의 상태값은 useState훅으로 관리되기 때문에 컴포넌트의 this로부터 자유롭다.
        또한 함수형 컴포넌트 자체와 함수형 컴포넌트 안에서 선언한 함수들 모두 전역 객체를 this로 가지기 때문에 애초에 this가 다 같다.
        그래서 이벤트 핸들러에 콜백 함수를 넘기는 상황에도 딱히 신경 쓸 필요가 없다.
            • const 키워드 + 함수 형태로 선언해야한다
            • 요소에 적용하기 위해 this가 따로 필요하지 않다

📌 HTML에서와의 차이점
    1) React 이벤트 이름은 소문자 대신 camelCase를 사용
    2) JSX에 문자열 대신 함수를 전달

    html에서는 아래와 같이 이벤트를 넣었다면,
```js
<button onClick="activateButton()">클릭하세요</button>
```
    React에서는 이벤트이름을 onClick, onSubmit 등과 같이 camelCase로 설정한다는 차이점이 있습니다. event handler는 JSX 표기인 { }를 사용하여 연결합니다.
```js
<button onClick={activateButton}>클릭하세요</button>
```

📌 Event Binding
    Event에서 가장 중요한 부분은 binding이다. binding이 중요한 이유는 binding을 따로 지정을 해주지 않으면 해당 method에서 호출하는 this가 해당 class 안에서의 event 값이 아닌 최상위인 windows에서 값을 가져올 수 있기 때문이다.

    Event Binding 방법
        🌱 Constructor에서 정의를 해주는 방법
        🌱 render function 안에서 정의를 해주는 방법
        🌱 ES6 화살표 함수를 사용하는 방법
        🌱 autobind-decorator 라이브러리를 사용하는 방법

    Event Binding를 하지 않아도 되는 경우
        🌱 this를 이용하여 해당 class 참조를 하지 않아도 되는 경우
        🌱 React.creatClass()를 사용하는 경우
        🌱 화살표 함수를 사용하는 경우
        🌱 같은 method를 여러 번 호출할 경우 생성자에서 한 번만 binding을 해서 중복 binding 행동을 줄이는 경우

### Quiz
    Q1. Hook의 장점 4가지는?
    Q2. 이벤트 핸들링과 HTML의 차이점 2가지는?