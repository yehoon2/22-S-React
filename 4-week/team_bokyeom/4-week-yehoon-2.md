# Hook(2)

**Hook의 특징**

- **Hook은 무조건 최상위 레벨에서만 호출해야 한다. → 반복문이나 조건문 또는 중첩된 함수 안에서 Hook을 호출하면 안 된다.**
- **리액트 함수 컴포넌트에서만 Hook을 호출해야 한다.**

**잘못된 Hook 사용법**


잘못된 이유: if문에 useEffect() Hook이 걸려서, 만약 if문이 false라면 Hook이 호출되지 않기 때문이다. 그렇게 되면 렌더링 할 때마다 Hook이 같은 순서로 호출되지 않는다.

## eslint-plugin-react-hooks

**:Hook의 규칙을 따르도록 강제해주는 프로그램**

**리액트 컴포넌트가 Hook의 규칙을 따르는지 아닌지 확인해준다.**

## Custom Hook

- Custom Hook의 이름은 꼭 use로 시작해야 한다!
- 여러 개의 컴포넌트에서 하나의 Hook을 사용할 때 컴포넌트 내부에 있는 모든 state와 effects는 전부 분리되어 있다.
- 각 Custom의 호출 또한 완전히 독립적이다.