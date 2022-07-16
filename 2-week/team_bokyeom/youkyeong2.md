# Javascript

- DOM+event
    
    ### DOM(문서객체모델)
    
    HTML, XML (eXtensible Markup Language: 사용자 정의 태그)문서의 프로그래밍 Interface (구조 제공)
    
    문서의 구조화된 표현 /저장 /조작 방식을 제공함으로 프로그래밍언어가 dom 구조에접근하여 원하는 event를 진행할 수 있게 도움
    
    HTML문서의 객체기반 표현 방식으로 nodes와 objects로 문서를 표현→HTML과 DOM이 비슷한측면도 있으나 web page를 scirpt or 프로그래밍언어로 사용가능하게 연결시켜주는 역할
    
    <자매품>
    
    - CSSOM(Cascading Style Sheets Object Model) – 요소들과 연관된 스타일 정보의 구조화된 표현
    
    →DOM tree와 CSSOM tree두 모델이 존재하면 Critical Rendering Path(웹페이지가 만들어지는 과정) 중 첫번째 단계에서 생성되는 렌더 트리를 생성할 수 있음
    
    [https://wit.nts-corp.com/2019/02/14/5522](https://wit.nts-corp.com/2019/02/14/5522)
    
    ### document객체
    
    :웹페이지 자체로서 웹페이지에 존재하는 HTML요소로의 접근을 위해서는 반드시 Document 객체부터 시작해야 한다.
    
    →method : 요소 선택/요소 생성/event handler추가/ 객체선택
    
    요소 선택:  태그이름, 아이디, 클래스, name속성값, 선택자
    
    요소 생성 : `document.createElement(생성요소),document.write(출력)`
    
    event handler추가: `document.getElementById(아이디).onclick = function(){ 실행할 코드 }`
    
    객체 선택 : 객체 집합(object collection)이용을 통해 손쉽게 html객체 선택 가능 [http://www.tcpschool.com/javascript/js_dom_document](http://www.tcpschool.com/javascript/js_dom_document)
    
    ### dom tree
    
    브라우저가 html문서를 로드한 이후에 파싱해서 생성하는 모델,
    
    객체의 트리로 구조화되어 dom tree 
    
    DOM tree의 진입점(Entry point)는 document 객체이며 최종점은 요소의 텍스트를 나타내는 객체이다.
    
    - DOM tree의 노드구성 [https://poiemaweb.com/js-dom](https://poiemaweb.com/js-dom)
        
        **문서 노드(Document Node)**
        
        트리의 최상위에 존재하며 각각 요소, 어트리뷰트, 텍스트 노드에 접근하려면 **문서 노드를 통해야 한다. 즉, DOM tree에 접근하기 위한 시작점(entry point)이다.**
        
        **요소 노드(Element Node)**
        
        요소 노드는 HTML 요소를 표현한다. HTML 요소는 **중첩에 의해 부자 관계**를 가지며 이 부자 관계를 통해 **정보를 구조화**한다. 따라서 요소 노드는 문서의 구조를 서술한다고 말 할 수 있다. **어트리뷰트, 텍스트 노드에 접근하려면 먼저 요소 노드**를 찾아 접근해야 한다. 모든 **요소 노드는 요소별 특성을 표현하기 위해 HTMLElement 객체를 상속한 객체로 구성**된다. (그림: DOM tree의 객체 구성 참고)
        
        **어트리뷰트 노드(Attribute Node)**
        
        어트리뷰트 노드는 HTML 요소의 어트리뷰트를 표현한다. 어트리뷰트 노드는 해당 어트리뷰트가 지정된 **요소의 자식이 아니라 해당 요소의 일부로 표현**된다. 따라서 **해당 요소 노드를 찾아 접근하면 어트리뷰트를 참조, 수정**할 수 있다.
        
        **텍스트 노드(Text Node)**
        
        텍스트 노드는 HTML 요소의 텍스트를 표현한다. 텍스트 노드는 요소 **노드의 자식이며 자신의 자식 노드를 가질 수 없다. 즉, 텍스트 노드는 DOM tree의 최종단**이다.
        
    
    주석을 포함한 html속 모든 것은 DOM을 구성한다.
    
    개발자 도구를 이용해서 Elements선택 후 우측 properties를 통해 DOM을 검사 및 수정가능
    
    ### 이벤트
    
    이벤트
    
    : 프로그램에서 일어나는 사건이나 발생으로 원한다면 응답까지 포함
    
    [https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks/Events](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks/Events)
    
    **이벤트 종류**
    
    마우스 / 키 / 폼 / 로드 및 페이지관련 이벤트
    
    [https://jenny-daru.tistory.com/17](https://jenny-daru.tistory.com/17)
    
    **이벤트 연결**
    
    • 사용자가 실제 이벤트를 발생시켰을 때 대응하여 처리하는 것  =>  '**이벤트 핸들러**'
    
    • '이벤트 핸들러'는 앞에 '**on**'을 붙여 주고 이벤트에 대한 동작(함수)을 처리
    
    - 미정의 되는 요소로 인한 문제 방지를 위해 'onload’
    
 
    
    해당 요소를 가져온 다음 이벤트를 추가해 함수를 실행하는 고전 방식
    
    ★ 인라인 방식과 고전 방식의 경우 같은 객체에 대해 동일한 이벤트를 여러 번 사용 불가 ★
    
    ### 이벤트 흐름
    
    표준 [DOM 이벤트](http://www.w3.org/TR/DOM-Level-3-Events/)에서 정의한 이벤트 흐름엔 3가지 단계가 있습니다.
    
    1. 캡처링 단계 – 이벤트가 하위 요소로 전파되는 단계
    2. 타깃 단계 – 이벤트가 실제 타깃 요소에 전달되는 단계
    3. 버블링 단계 – 이벤트가 상위 요소로 전파되는 단계
    
    **버블링**
    
    브라우저는 특정 화면 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 화면 요소까지 이벤트를 전파시킴
    
    focus와 같이 버블링 되지 않는 이벤트도 존재하지만 거의 모든 이벤트는 버블링 된다.
    
    event.stopPropagation() ->버블링 중단
    
    `<body onclick="alert(버블링은 여기까지 도달하지 못합니다.)">
    <button onclick="event.stopPropagation()">클릭해 주세요.</button>
    </body>`
    
    **캡쳐링**
    
    버블링과 비교하여 이용빈도가 적음.
    
    `on<event>` 프로퍼티나 HTML 속성, `addEventListener(event, handler)`
    를 이용해 할당된 핸들러는 타깃 단계와 버블링 단계)에서만 동작→캡처링 단계에서 이벤트를 잡아내려면 `addEventListener`의 `capture` 옵션을 `true`
    
- const, let, var
    
    ### 변수
    
    variable(변수) : **하나의 값을 저장하기 위해 확보한 메모리 공간 자체/ 공간 식별을 위해 붙인 이름**
    
    변수에 값을 저장하는 것을 **할당** (assignment, 대입, 저장)
    
    변수에 저장된 값을 읽어 들이는 것을 **참조** (reference)
    
    변수명을 자바스크립트 엔진에 알리는 것을 **선언** (declaration)
    
    변수의 선언은 `var`, `const`, `let` 키워드로 가능.  ES6에서 const와 let이 추가
    
    - **선언 단계**: 변수명을 등록하여 자바스크립트 엔진에 변수의 존재를 알린다.
    - **초기화 단계**: 값을 저장하기 위한 메모리 공간을 확보하고 암묵적으로 undefined를 할당해 초기화한다.
    
    ### 호이스팅
    
    변수 선언이 어디에 있든 상관없이 다른 코드보다 먼저 실행되는 특징을 **호이스팅(hoisting)**
    
    변수 선언 뿐만 아니라, `var`, `let`, `const`, `function`, `function*`, `class` 키워드를 사용해 선언한 모든 식별자(변수, 함수, 클래스 등)는 호이스팅이 된다.
    
    변수에 값을 할당 할 때에는 할당 연산자(=)를 사용
    
    변수에는 재할당도 가능한데 변경이 안된다면, 변수가 아닌 상수(constant)라 부른다.
    
    변수 선언과 할당은 하나의 문(statement)으로 단축 표현할 수 있지만, 변수 선언이 호이스팅되어 런타임 이전에 실행되고 값의 할당은 소스코드가 순차적으로 실행되는 런타임에 실행된다.
    
    ### 스코프
    
    스코프(scope)는 식별자(ex. 변수명, 함수명, 클래스명 등)의 유효범위를 뜻하며, 선언된 위치에 따라 유효 범위가 달라진다. 전역에 선언된 변수는 전역 스코프를, 지역에 선언된 변수는 지역 스코프를 갖는다.
    
    JS내 모든 코드 블록(if, for, while, try/catch 등)이 지역 스코프 생성 →**블록 레벨 스코프**
    
    var 선언된 변수는 오로지 함수의 코드 블록만을 지역 스코프로 한정 → **함수 레벨 스코프**
    
    **재할당의 문제를 고려해서 함수 코드 블록만을 지역 스코프로 인정하는 `var` 대신, 블록 레벨 스코프를 지원하는 `const`와 `let`을 사용하는 것을 권장한다.**
    
    변수의 스코프는 최대한 좁게 만드는 것을 권장→ , var 키워드 보다는 let과 const 키워드를 사용하며, 변경하지 않는 값(상수)이라면 const 키워드를 사용하는 것이 안전하다.
    
    ### var
    
    - 변수 중복 선언 가능하여, 예기치 못한 값을 반환할 수 있다.
    - 함수 레벨 스코프로 인해 함수 외부에서 선언한 변수는 모두 전역 변수로 된다.
    - 선언 단계와 초기화 단계가 동시에 진행되어, 암묵적으로 undefined 할당해 초기화→변수 선언문 이전에 변수를 참조하면 undefined를 반환
    
    ### let
    
    - 변수 중복 선언이 불가하지만, 재할당은 가능하다.
    - **선언 단계와 초기화 단계가 분리되어 진행→** 스코프의 시작 지점부터 초기화 단계 시작 지점까지 변수를 참조할 수 없는 **일시적 사각지대(Temporal Dead Zone: TDZ)**
     구간에 존재
    
    ### const
    
    - **반드시 선언과 초기화를 동시에 진행되어야 한다.→런타임 이전에 실행불가**
    - 재선언 불가, 재할당 불가(원시값의 재할당 불가, 객체의 재할당 가능)
    
    
- Callback, promise, Async-Await, 동기 비동기, 블로킹 논블로킹
    
    ### Callback()
    
    **callback :파라미터로 함수를 전달받아, 함수의 내부에서 실행하는 함수**
    
    순차적으로 코드를 실행하고 싶은 경우에 사용한다.
    
    직접 정의 가능, 다른 곳에서 만든 함수 사용가능
    
    가독성이 떨어질 뿐만 아니라 에러 및 예외처리가 어렵다는 단점
    
    ```jsx
    function whatYourName(name, callback) {
        console.log('name: ', name);
        callback();
    }
    
    function finishFunc() {
        console.log('finish function');
    }
    
    whatYourName('miniddo', finishFunc);
    
    <output>
    name: miniddo
    finish function
    
    함수를 인자로 사용할 때 함수명()를 붙일 필요가 없이 함수명만 사용가능
    ```
    
    아무 method에서나 callback함수를 사용할 수 있는 것은 아니고 사용이 가능한 함수가 존재함
    
    - setTimeout(callback,1000);//1초 후에 callback함수 실행
    - addEventListener('click', callback)//click하면 callback
    
    **콜백지옥 (Callback Hell)**
    
    비동기 호출이 자주 일어나는 프로그램의 경우 '콜백 지옥'이 발생한다.
    
    함수의 매개변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들어질 정도로 깊어지는 현상이다.
    
    → `Promise` 
    
    ### promise
    
    **프로미스는 비동기 작업의 단위로서 비동기 호출 시, 마치 동기 호출 처럼 값(프로미스)을 반환**
    
    (nested promise방식, promise chaining방식)
    
    - 비동기 작업 실행시 표준화 된 방식으로 성공(then) 및 실패(catch) 여부를 처리가능+finally(성공 및 실패여부와 상관없이 실행)존재
    - 프로미스로 생성된 비동기 인스턴스는 한 번만 실행
    - promise도 callback함수를 사용하는 object이기때문에 promise의 사용이 많아지는 경우에는 가독성이 떨어지는 callback hell
    
    ### async함수와 await
    
    **[async 함수](https://ko.javascript.info/async-await#ref-182)**
    
    - 함수 앞에 async를 붙이면 해당 함수는 항상 프라미스를 반환하는 비동기작업을 진행합니다.
    - 프라미스가 아닌 값을 반환하더라도 이행 상태의 프라미스(resolved promise)로 값을 감싸 이행된 프라미스를 반환
    
    **[await](https://ko.javascript.info/async-await#ref-183)**
    
    - `await`는 `async` 함수 안에서만 동작, js에서 `await` 키워드를 만나면 프라미스가 처리될 때까지 대기
    - '중단’된 처리는 프라미스가 처리되면 실행이 재개
    - 프라미스가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을 할 수 있기 때문에, CPU 리소스가 낭비되지 않습니다.
    - **`await`는 최상위 레벨 코드에서 작동하지 않습니다 (**하지만 익명 async 함수로 코드를 감싸면 최상위 레벨 코드에도 `await` 사용가능)
    - `await`는 `promise.then`보다 가독성이 좋음.
    
    ### 동기와 비동기
    
    **동기(synchronous : 동시에 일어나는)**
    
    요청과 그 결과가 동시에 일어난다는 약속으로 요청을 하면 시간이 얼마가 걸리던지 요청한 자리에서 결과가 주어져야 합니다. 트랜잭션(쪼갤 수 없는 업무 처리의 최소 단위) 동시로 맞춤 
    
    - 장점: 설계가 간단하고 직관적
    - 단점: 결과가 주어질 때까지 대기
    
    **비동기(Asynchronous : 동시에 일어나지 않는)**
    
    요청과 결과가 동시에 일어나지 않을거라는 약속입니다.요청한 그 자리에서 결과가 주어지지 않음노드 사이의 작업 처리 단위를 동시에 맞추지 않아도 된다.
    
    - 단점: 동기와 비교하여 상대적으로 복잡, 의존성이 길게이어진 작업처리에 까다로움
    - 장점: 시간이 걸리더라도 다른 작업을 할 수 있으므로 자원을 효율적으로 사용
    
    ### 블로킹과 논블로킹
    
    **블로킹**
    
    A함수가 B함수를 호출하는 경우, 제어권(코드를 실행할 권리)을 A → B함수에게로 넘겨 주는 것이다.
    
    A함수는 함수실행을 잠시 멈추고 B함수가 코드를 전부 실행한 이후에는 제어권을 A에게로 돌려줘 A함수를 마저 실행하는 과정을 거친다.
    
    **논블로킹**
    
    A함수가 B함수를 호출해도 제어권을 A함수가 그대로 갖고 있다.
    
    따라서 B함수가 실행되지만, B함수 호출 이후에도 A를 계속 실행한다.
    
    **A 함수는 B 함수의 리턴값이 필요한 경우**
    
    Sync-Blocking : 제어권을 b에게 넘겨주고 B의 실행이 완료되면 제어권과 return값을 받아서 실행하면 된다.
    
    Async-blocking:  A 함수는 B 함수에게 제어권을 보낸다. 따라서 작업을 기다려야함
    
    Sync-Nonblocking : A함수가 B함수에게 제어권을 주지 않고 자신의 코드를 계속실행하면서 실행 중간마다 B함수에게 실행완료여부를 물어봄
    
    Async-Nonblocking: B함수 호출 이후에도 자신의 코드를 계속 실행, B함수를 호출할때 콜백함수를 함께 주며, B함수는 작업을 마치고 A로부터 전달받은 콜백함수실행