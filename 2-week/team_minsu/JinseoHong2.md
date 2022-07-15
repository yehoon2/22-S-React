# DOM

[[JavaScript] DOM이란 무엇인가?](https://m.blog.naver.com/magnking/220972680805)

DOM 이란 Document Object Model. 문서 객체 모델.

문서 객체란 html 문서의 태그들을 JavaScript가 이용할 수 있는 객체로 만든 것.

DOM은 그 문서객체를 인식하는 방식.

넓은 의미로 DOM 은 웹 브라우저가 HTML 페이지를 인식하는 방식을 말함. 좁은 의미로는 객체와 관련된 객체의 집합.

## 어떻게 생겼나?

DOM은 tree 형식의 자료구조를 가지고 있음.

하나의 root node에서 시작됨.

위쪽의 node는 부모, 아래 node는 자식. 자식이 없는 노드는 leaf node.

모든 개개의 개체를 노드라고 표현함. 태그 뿐 아니라 태그 안의 텍스트나 속성 등도 이에 속함

원래 HTML 페이지에 없던 문서객체를 JavaScript를 이용해서 생성할 수 있음.

동적으로 문서 객체 생성.

[DOM 소개 - Web API | MDN](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)

[JavaScript HTML DOM](https://www.w3schools.com/js/js_htmldom.asp)

With the object model, JavaScript gets all the power it needs to create dynamic HTML:

- JavaScript can change all the HTML elements in the page
- JavaScript can change all the HTML attributes in the page
- JavaScript can change all the CSS styles in the page
- JavaScript can remove existing HTML elements and attributes
- JavaScript can add new HTML elements and attributes
- JavaScript can react to all existing HTML events in the page
- JavaScript can create new HTML events in the page

## What is the HTML DOM?

The HTML DOM is a standard **object** model and **programming interface** for HTML. It defines:

- The HTML elements as **objects**
- The **properties** of all HTML elements
- The **methods** to access all HTML elements
- The **events** for all HTML elements

In other words: **The HTML DOM is a standard for how to get, change, add, or delete HTML elements.**

## HTML LifeCycle

HTML 의 생명주기는 3개의 중요한 이벤트를 가짐.

- DOMContentLoaded : 브라우저에서 HTML 이 완전히 로드되고 DOM tree가 만들어질 때 발생.
- load : 문서의 모든 콘텐츠(image, scrip, css, etc)가 로드된 후 발생하는 이벤트
- beforeunload/unload : 사용자가 페이지를 벗어날 때 일어나는 이벤트

### DOMContentLoaded

위 이벤트는 onload 이벤트보다 먼저 발생함. 빠른 실행 속도가 필요할 때 적합

```jsx
window.addEventListener('DOMContentLoaded', funtion(){
});
```

### load

위 이벤트는 문서의 모든 콘텐츠가 로드 된 후 발생하는 이벤트. 불필요한 로딩 시간이 추가될 수 있음. 문서에 onload는 하나만 존재해야함. 중복될 경우, 마지막 선언이 실행. 외부 라이브러리에서 선언된 경우 이를 하나로 합쳐야함.

```jsx
//방법 1
window.onload = funtion(){
alert('Page loaded');
};
//방법 2
<body onload='실행 코드'>
```

### beforeunload/unload

사용자가 해당 페이지를 떠날 때. / 해당 페이지를 떠난 후 통계 전송과 같은 일부 작업을 할 때.

```jsx
window.onbeforeunload = function () {
  return "변경 사항을 저장하지 않았습니다. 정말 지금 나가시겠습니까?";
};
```

```jsx
let analyticsData = {
  /* 수집하는 object data */
};

window.addEventListener("unload", function () {
  navigator.sendBeacon("/analytics", JSON.stringify(analyticsData));
});
```

# 이벤트 핸들링

[[JS] 이벤트 핸들링과 바인딩, 이벤트 흐름](https://victorydntmd.tistory.com/85)

JS 코드의 대부분은 이벤트에 의해 동작함.

이벤트: 클리그, 키보드 입력 등 사용자의 행위.

이벤트 핸들링: 이러한 이벤트를 처리하는 것.

이벤트 핸들링의 과정

1. 이벤트를 받아줄 요소를 선택
2. 그 요소가 어떤 이벤트에 반응할지 서로 연결해주는 바인딩
3. 이벤트 발생시 실행될 코드 작성.

### 바인딩

요소와 이벤트를 연결해주는 것.

방법들

1. HTML 이벤트 핸들러

HTML 요소의 onclick 속성에 JS 함수 호출하여 바인딩

```html
<button class="btn" onclick="myFunction()"></button>
```

클릭시 myFuntion() 이라는 함수 실행.

하지만 HTML과 JS는 분리해서 관리하는 것을 권장. 좋은 방법은 아님.

1. DOM 이벤트 핸들러

DOM 요소에 이벤트를 바인딩. 이후 발생시 실행될 코드 작성.

```jsx
element.onclick = myFunction(){...}
```

이 방법도 권장하지 않음

1. DOM 이벤트 리스너.

DOM 요소에 addEventListener 메서드 호출하여 이벤트 바인딩.

```jsx
element.addEventListener("event", myFunction(){...}, [,boolean]);
```

이 방식이 바닐라 JS 기준으로 가장 많이 사용하는 방식.

3번째 매개 변수는 이벤트 흐름을 true or false로 정함.

### 동적으로 요소 생성시 이벤트 바인딩 이슈 - rebinding

바인딩 코드 장성시 HTML 문서 로딩될 때 해당 요소마다 이벤트가 바인딩되고 사용자에 의해 이벤트가 발생되길 기다림.

하지만 createTextNode() 메서드 jQuery append(), after() 메서드와 같이 동적으로 요소를 생성하면 이벤트 바인딩이 적용되지 않음.

동적으로 추가한 요소는 이벤트를 다시 바인딩 해야함.

### 이벤트 흐름 - Event Bubbling, Event Capturing

DOM 은 tree 구조이다. 따라서 어떤 요소에 대해 어떤 이벤트가 발생하면 그 요소의 부모도 같은 이벤트의 영향을 받게 됨.

이러한 이벤트 흐름을 이벤트 버블링이라고 함.

반대되는 개념은 이벤트 캡쳐링이 있다. 자식으로 이벤트가 연계되는 이벤트 흐름이다.

DOM addEventListener 에서 3번째 매개변수 값의 의미

- false - Event bubbling
- ture - Event Capturing

# ES6 문법

[[JavaScript] 자주 사용하는 ES6 문법 정리](https://velog.io/@kimhscom/JavaScript-%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-ES6-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%A6%AC)

ES6는 아래의 새로운 기능들을 포함하고 있습니다.

- const and let
- Arrow functions(화살표 함수)
- Template Literals(템플릿 리터럴)
- Default parameters(기본 매개 변수)
- Array and object destructing(배열 및 객체 비구조화)
- Import and export(가져오기 및 내보내기)
- Promises(프로미스)
- Rest parameter and Spread operator(나머지 매개 변수 및 확산 연산자)
- Classes(클래스)

## const & let

const 는 변수 선언을 위한 새로운 키워드.

일단 사용되면 변수를 다시 할당할 수 없음. 변경 불가능한 변수.

```jsx
// ES6
const MyBtn = document.getElementById("mybtn");
```

let은 새로운 값을 가질 수도 있고 재할당도 가능함. 변경 가능한 변수 생성.

```jsx
let name = "철수";

name = "영희";

console.log(name);
// 출력 => 영희
```

둘 다 블럭범위이다. 범위 내에서만 사용할 수 있음.

## Arrow functions

```jsx
// ES5
var x = function (x, y) {
  return x * y;
};

// ES6
const x = (x, y) => x * y;
```

기존에 function과 return 을 사용하지 않고 ⇒ 를 통해 함수를 활용할 수 있음.

## Template Literals

문자열을 연결하기 위해 + 연산자를 사용하지 않으며, 백틱(`)을 사용해 문자열 내에서 변수 사용 가능.

```jsx
// ES5
function myFunc1() {
  return "안녕" + name + "너의 나이는" + age + "살 이다!";
}

console.log(myFunc1("영희", 22));
// 출력 => 안녕 영희 너의 나이는 22살 이다!

// ES6
const myFunc = (name, age) => {
  return `안녕 ${name}, 너의 나이는 ${age}살 이다!`;
};

console.log(myFunc1("영희", 22));
// 출력 => 안녕 영희, 너의 나이는 22살 이다!
```

## Default parameters (기본 매개 변수)

매개 변수를 쓰지 않은 경우 매개 변수가 이미 기본값에 정의되어 있을때 undefined를 반환하지 않음.

```jsx
const myFunc = (name, age = 22) => {
  return `안녕 ${name} 너의 나이는 ${age}살 이니?`;
};

console.log(myFunc1("영희"));
// 출력 => 안녕 영희 너의 나이는 22살 이니?
```

오류를 미리 처리 가능.

## Array and object destructing(배열 및 객체 비구조화)

비구조화를 통해 배열 또는 객체의 값을 새 변수에 더 쉽게 할당 가능.

```jsx
// ES6 문법
const contacts = {
  famillyName: "이",
  name: "영희",
  age: 22,
};

let { famillyName, name, age } = contacts;

console.log(famillyName);
console.log(name);
console.log(age);
// 출력
// 이
// 영희
// 22
```

기존에는 각 변수에 각 값을 할당했지만, ES6에서는 객체의 속성을 얻기 위해 값을 중괄호 안에 넣음.

배열의 경우에는 중괄호 대신 대괄호를 사용함.

## Import and export(가져오기 및 내보내기)

예를 들어, 두 개의 파일이 있습니다. 첫 번째 파일은 `detailComponent.js`이고 두 번째 파일은 `homeComponent.js`입니다.

`detailComponent.js`에서는 `detail` 함수를 내보낼 예정입니다.

```jsx
// ES6
export default function detail(name, age) {
  return `안녕 ${name}, 너의 나이는 ${age}살 이다!`;
}
```

그리고 `homeComponent.js`에서 이 기능을 사용하려면 `import`만 사용합니다.

```jsx
import detail from "./detailComponent";

console.log(detail("영희", 20));
// 출력 => 안녕 영희, 너의 나이는 20살 이다!
```

둘 이상의 모듈을 가져오려는 경우, 중괄호에 넣기만 하면 됩니다.

```jsx
import { detail, userProfile, getPosts } from "./detailComponent";

console.log(detail("영희", 20));
console.log(userProfile);
console.log(getPosts);
```

### Promises (프로미스)

비동기 코드를 쓰는 방법.

API 에서 데이터를 가져오거나 실행하는데 시간이 걸리는 함수를 가지고 있을 때 사용.

```jsx
const myPromise = () => {
  return new Promise((resolve, reject) => {
    resolve("안녕하세요 Promise가 성공적으로 실행했습니다");
  });
};

cosole.log(myPromise());
// Promise {<resolved>: "안녕하세요 Promise가 성공적으로 실행했습니다"
```

## Rest parameter and Spread operator(나머지 매개변수 및 확장 연산자)

Rest parameter 는 배열의 인수를 가져오고 새 배열을 반환하는데 사용.

Spread operator는 Rest parameter와 구문이 동일하지만 spread operator는 배열 자체를 가짐.

## Classes(클래스)

```jsx
class myClass {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const user = new myClass("영희", 22);

console.log(user.name); // 영희
console.log(user.age); // 22
```

여기서 클래스는 object가 아닌 JS object의 template임.

# Callback, Promise, Acync-Await

[자바스크립트 비동기통신 Callback, Promise, Async/Await 이해하기](https://techlog.io/Javascript/General/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%B9%84%EB%8F%99%EA%B8%B0%ED%86%B5%EC%8B%A0-callback-promise-async-await-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/)

JS는 싱글 스레드 언어 → 한번에 한개의 일만 순차적으로 처리할 수 있음.

따라서 병렬처리가 필요한 작업들을 “asynchronos non-blocking I/O model”이라는 방식을 통해 해결.

언어 자체는 병렬처리가 불가능하나 엔진에서는 I/O 관련 작업들을 내부적으로 병렬처리.

## Callbacks

JS 는 함수가 받는 값을 함수로도 받을 수 있음.

Callback : 인자로 받아들인 함수를 다시 호출하는 기능

```jsx
function add5(a, callback) {
  setTimeout(() => callback(a + 5), 100);
  // 100ms가 지난 후 함수로 입력받은 callback에 a + 10값을 다시 입력하여 callback함수 호출
}
add5(10, function (res) {
  // add5가 입력받는 callback함수 정의 부분
  console.log(res);
});
```

연속적으로 사용하게 되면 유지보수가 힘들어짐.

## Promises

Promise 란 기본적으로 callback 이 하는 일과 같다.

차이점 : Promise 는 자체 메서드인 .then() 을 호출

```jsx
function add10(a) {
  return new Promise((resolve) => setTimeout(() => resolve(a + 10), 100));
} //Promise사용 시 작업이 끝났음을 알려주는 resolve를 인자로 받아들임.

add10(10)
  .then(add10)
  .then(add10)
  .then(add10)
  .then((res) => console.log(res));
```

then() 과 같은 메서드를 연속적으로 사용가능하다는 이점.

callback 보다 작성하고 이해하기 쉬움.

예외처리

```jsx
add10(10)
  .then((res) => {
    throw "test error";
  })
  .catch((err) => console.log(err));
```

작업이 실패하면 자동으로 .catch 메서드가 호출됨. if-else 를 사용하지 않고 한번에 해결 가능.

기존 try-catch를 이용가능하나 warning message 출력.

## Async / Await

```jsx
async function f1() {
  const a = await add10(10);
  const b = await add10(a);
  console.log(a, b);
}
f1();
```

우선 함수 앞에 async 키워드 사용. 선언된 함수 안에서만 await 키워드 사용가능.

promise 보다 쉽게 비동기적인 상황 표현 가능.

await 은 함수의 작업이 끝나고 결과값을 반환할 때까지 대기.

결과값 리턴시 다음작업으로 넘어감.

예외처리

```jsx
async function f2() {
  const a = await add10(10).then((res) => res);
  const b = await add10(a).catch((err) => err);
  console.log(a, b);
}
f2();
```

.catch 를 사용하여 예외처리 가능.
