# DOM (Document Object Model : 문서 객체 모델)

## 정의	

(html, xml 등의)문서에 대한 모든 내용을 담고 있는 문서용 API <br>
텍스트 파일로 만들어진 문서를 브라우저가 이해할 수 있도록 구성한 것 <br>
구성 : html 요소간의 부자관계를 반영하여 모든 노드들을 트리 구조로 함
	
## 문서용 API
- 해당 요소를 나타내는 노드
- 노드의 속성을 나타내는 프로퍼티         
- 이를 조작할 수 있는 여러 메소드	

  --> 이것들을 담아 구조화한 객체


![DOM TREE](https://postfiles.pstatic.net/MjAyMTEyMTRfODUg/MDAxNjM5NDc0ODAyMTgx.Pb4skE5ixZxeScwx0gIWJfYzzxakGdlEztGG5wuDaNQg.UB_NtDRNVh8zGbgty0C1txOEaSnnCtBA7_9WX9tRN7sg.PNG.watermoon14/DOM.png?type=w773)

## DOM TREE 
DOM : html 요소간의 부자관계를 반영하여 모든 노드들을 트리 구조로 구성한 것 <br>
html의 요소중 attribute는 attribute노드로, text content는 text노드로 변환 <br>
이를 렌더링 엔진이 파싱하여 노드 객체로 구성된 트리구조를 가진 DOM을 생성한다.

노드tree의 최상위 노드를 root라고 하며, HTML문서에서 <html>이 root 노드가 된다. <br>
트리의 시작은 Doument이며, 각각의 노드의 타입에 따라 element, attribute, text 노드로 분류된 계층 구조를 가진다. <br>
text 노드가 각 노드tree의 리프 노드(마지막 노드)가 된다.


## NODE
노드 객체는 총 12개의 종류가 있고, 프로토타입에 의한 상속 구조를 가진다. <br>
모든 노드 객체는 Object, EventTarget,Node interface를 상속 받는데 <br>
EventTarget은 addEventListner, removeEventListener와 같은 기능을 제공한다.<br>
Node interface는 parent나 child 노드 같은 기능을 제공한다.
	
#### 주요 노드 4가지
1.	문서 노드(document node)
    -  DOM tree 최상위 root 노드로 document 객체를 가르킴
2.	요소 노드(element node)
    - html 요소를 가르키는 객체로 문서의 구조를 표현
3.	속성 노드(attritbue node)
    - 지정된 html 요소 노드와 형제 관계를 가지지만 지정된 html 요소 노드의 부모 노드에는 접근하지 않기 때문에 변경을 위해서는 먼저 형제노드에 접근해야 한다
4.	텍스트 노드(text node)
    - 자식을 가질 수 없는 리프 노드
    - 접근하기 위해서는 먼저 부모 노드인 요소 노드에 접근해야 한다

# Event Handling
evnet
- 어떤 대상(버튼, 텍스트 상자 등 = component(컴포넌트)에 사용자가 액션을 취하는 것

event handling
- 이벤트가 발생했을 때 지정된 특정 작업을 수행하는 것 <br>
ex) 버튼 클릭 시 메시지 출력, 패스워드 입력 시 규칙 판별, 마우스 오버 시 이미지를 교체


# ES6
- ECMAScript의 6번째 버전
  - 여러 자바스크립트 라이브러리 (React, Vue)등 프레임 워크가 ES6기반에서 구성되어 있어 대중적으로 사용하고 있습니다. 

- ECMAScript
  - Ecma international이 ECM-262 기술 규격에 따라 정의하고 있는 표준화된 스크립트 프로그래밍 언어를 말합니다.
	
- 주요 기능
	-	let, const
	-	백틱 ``
		-	`  `(백틱)사이에 변수값을 넣을려면 ${ ...} 로 사용하면 됩니다.
  -	화살표 함수
    - function키워드 대신 화살표를 사용하여 보다 간략하게 함수를 표현하는 함수 표현식입니다.

# 비동기 처리 
특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성

### 비동기 처리 예시
setTimeout
- 시간을 설정하고, 그 시간이 경과되면 딱 한번 전달받은 콜백함수가 실행되게
하는 함수
```js
setTimeout(()=>console.log("1초 뒤에 실행"), 1000);
console.log("!!!");
```

setInterval
- 시간 간격을 설정하고, 그 간격이 지날때마다 계속 콜백함수가 호출되게 하는 함수
```js
let handler = setInterval(()=>console.log("1초마다 실행"), 1000);
console.log("!!!");
```

process.nextTick
- 실행을 지연시켜서 동작순서를 바꿔버린다.
```js
function foo(){
  console.log("foo");
}

function bar(){
  console.log("bar");
}

process.nextTick(foo);
bar(); 
// bar가 먼저 출력됨
```


ajax
```js
function getData() {
  var tableData;
  $.get("https://domain.com/product/1", function(response) {
    tableData = reponse;
  });
  return tableData;
}

console.log(getData()); //undefined
```

- $.get( )으로 통신을 하여 서버에서 데이터를 받아왔고 response 인자에 담겨졌다
- 그 다음 데이터를 tableData라는 변수에 저장했다	
- 하지만 getData를 출력했을 때 데이터는 담겨져있지 않았다. <br>	
==> 비동기 처리가 되어 데이터를 받기도 전에 console.log를 하였기 때문	

### 동기 실행과 비동기 실행 차이
	

순서대로 결과가 출력되는 동기와 다르게 비동기는 몰아서 빨리 하기 좋은 작업들을 한꺼번에 하고, 나머지를 수행한다.

```js
let num = 1;

setTimeout(() => {
  num = 2;
}, 0);

num = 3;
console.log(num);
```
- 다음 예제와 같이 setTimeout 비동기함수가 0밀리초라도 콘솔에는 3이 출력된다.
- 먼저 자바스크립트 코드를 쭉 실행하고, 그 후에 EventLoop에서 각각의 콜백들에 대한 실행 여부를 판단하기 때문이다.

### 콜백 함수
비동기 처리 방식의 문제점 해결 <br>
콜백 함수(callbackFunc)를 사용하면 특정 로직이 끝났을 때 원하는 동작을 실행시킬 수 있다.

### 콜백 지옥
- 비동기 처리 로직을 위해 콜백 함수를 연속해서 사용할 때 발생하는 문제
- 가독성이 떨어지고 로직을 변경하기 어려워짐(콜백안에 콜백이 무는형식)

### Promise
콜백지옥 해결법

- 자바스크립트 비동기 처리에 사용되는 객체
- 사용 이유 : 비동기처리는 실행이 빠르다는 장점이 있지만 Ajax에서 보았듯이 $.get으로 데이터를 받아오기도 전에 화면에 출력이 되버려서 오류가 생길 수 있음

#### Promise의 3가지 상태
	Pending(대기)
		비동기 처리 로직이 아직 완료되지 않은 상태
	Fulfilled(이행)
		비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
	Rejected(실패)
		비동기 처리가 실패하거나 오류가 발생한 상태

Pending
- new Promise( ) 매서드를 호출하면 pending 상태가 된다
- new Promise( ) 매서드를 호출할 때 콜백 함수를 선언할 수 있고,
	콜백 함수의 인자로는 resolve, reject이다.
```js
new Promise(function(resolve, reject)){
  //...
});
```

Fulfilled
-	콜백 함수의 인자 resolve를 실행하면 Fulfilled 상태가 된다
-	이행 상태에서 then( )을 이용하여 처리 결과 값을 받을 수 있다.
```js
function getData() {
  return new Promise(functoin(resolve, reject){
    var data = 100;
    resolve(data);
  });
}

getData().then(function(resolveData) {
  console.log(resolveData);
});
```

Rejected
-	new Promise( )의 콜백 함수 인자로 reject를 호출하면 rejected상태가 된다
-	Rejected 상태 시 실패한 이유를 catch( )로 받을 수 있다.
```js
function getData() {
  return new Promise(functoin(resolve, reject){
    reject(new Error("Request is failed"))
  });
}

getData().then(function(err) {
  console.log(err);
});
```

# async-await
- 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법

- 기존의 비동기 처리 방식인 콜백 함수와 프로미스의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성할 수 있게 도와줍니다.

- 비동기 처리 메서드가 꼭 프로미스 객체를 반환해야 await가 의도한 대로 동작합니다.
- 사용법
```js
async function 함수명() {
  await 비동기_처리_매서드_명();
}
```

# JS의 기본 자료형
- 숫자형
  - 정수, 부동 소수점 숫자 등의 숫자를 나타낼 때 사용합니다. 정수의 한계는 ±253 입니다.
- bigint
	- 길이 제약 없이 정수를 나타낼 수 있습니다.
	- BigInt형 값은 정수 리터럴 끝에 n을 붙이면 만들 수 있습니다.
		
- 문자형
	-	빈 문자열이나 글자들로 이뤄진 문자열을 나타낼 때 사용합니다.
	
- boolean형
	- true, false를 나타낼 때 사용합니다.
- null
	- 알 수 없는 값을 나타냅니다. (비어 있는, 알 수 없는, 존재하지 않는)
	- typeof연산에서 object로 나오지만 이는 언어상의 오류로 객체가 아닙니다.
- undefined
	- 할당되지 않은 값을 나타냅니다
- 객체형
	- 복잡한 데이터 구조를 표현할 때 사용합니다.
	- 키로 구분된 데이터 집합이나 복잡한 개체(entity)를 저장할 수 있다.
  - 객체는 중괄호 {…}를 이용해 만들 수 있습니다.<br> 중괄호 안에는 ‘키(key): 값(value)’ 쌍으로 구성된 프로퍼티(property) 를 여러 개 넣을 수 있는데, 키엔 문자형과 심볼형, 값엔 모든 자료형이 허용됩니다.

```js
let user = {
  name : "John",
  age : 30
};
```

    첫 번째 프로퍼티 – "name"(키)과 "John"(값)
    두 번째 프로퍼티 – "age"(키)과 30(값)

<br>
<br>

```js
let id = Symbol();
// id는 새로운 symbol이 됩니다.
```		
- 심볼형
	-	객체의 고유 식별자를 만들 때 사용합니다.
  - 괄호 안에 심볼 이름이라  불리는 설명을 붙일 수도 있습니다.
  - 심볼은 유일성이 보장되는 자료형이기 때문에, 설명이 동일한 심볼을 여러 개 만들어도 각 심볼값은 다릅니다. 
  - 심볼에 붙이는 설명(심볼 이름)은 어떤 것에도 영향을 주지 않는 이름표 역할만을 합니다.
  - 문자열과 심볼은 서로의 타입으로 자동 형 변환되지 않습니다.

#### 변수
- 자료형에 관계 없이 모든 데이터일 수 있습니다.
	


#### 동적 타입 언어
  JS는 자료의 타입은 있지만 변수에 저장되는 값의 타입은 언제든지 바꿀 수 있는 동적 타입 언어입니다. 

# Prototype
- Prototype Link와 Prototype Object가 존재

- Prototype Object
	-	객체는 언제나 함수로 생성
  - personObject는 Person이라는 함수로 생성된 객체이고
  - 객체는 함수에서 시작
  ```js
  function Person() {}; //함수입니다.

  var personObject = new Person(); //함수로 객체를 생성했습니다.
  ```

- Prototype Object는 기본적인 속성으로 constructor와 __proto__를 가짐
  - constructor	
    - Prototype Object와 같이 생성되었던 함수
  - __proto__
    - Prototype Link입니다.

- Prototype Link
  - __proto__속성은 모든 객체가 빠짐없이 가지고 있는 속성입니다.
  - __proto__는 객체가 생성될 때 조상이었던 함수의 Prototype Object를 가리킵니다.
  - 즉 Prototype Object에서 설정한 것이 있다면 상속받아 사용할 수 있습니다.


#### Class
- Class는 prototype을 베이스로 문법만 추가된 것


# Property
- JS에서 노드는 각각의 정해진 property를 가지며, 그것을 제어할 수 있습니다.
- property는 이름(string 이나 symbol)과 값(원시함수(primitive), 메서드(method))을 가지고 있습니다.
- property는 어떤 값을 나타내는데, 이 값이 다른 값과 연관되어 있을 때 property라고 부릅니다. <br>

예)
```js
const str = "문자수";

console.log(str.length);
```

문자열에는 length라는 property가 포함되어 있는데 이 프로퍼티는 문자열 안에 있는 문자의 양을 정수로 나타낸 값을 담고 있습니다.

#### Instance property
- 특정 object instance의 특정한 데이터를 가지고 있습니다.
- Javascript에서 class를 정의한 후 그 클래스의 인스턴스를 생성한 다음 접근할 수 있는 프로퍼티를 의미합니다. 

- Instance property 정의법
  - 생성자 (constructor)를 사용한 방법

```js
class Student{
  constructor() {
    this.Name = "장범준"
  }
}
```

- Instance property 접근법
	- 정의한 클래스의 인스턴스를 new 키워드로 생성한 후 접근할 수 있습니다. 

Instance propety에 접근한 뒤 console.log로 출력한 예시
```js
const stu = new Student();

console.log(stu.Name); //장범준이 출력됨
```

Instance property는 클래스를 통해서 접근할 수는 없습니다.	

```js
console.log(Student.Name); //undefined
```

- Static Property (Class property)
	- 모든 object instance들에게 공유되는 데이터를 가지고 있습니다.
  - 클래스에 고정되어 있는 프로퍼티를 의미합니다. 그래서 인스턴스를 생성해서는 접근할 수 없고 클래스 이름을 통해서 접근할 수 있습니다. 

  - 정의법
```js
class Student{
  static Name = "권정열"
}
``` 
정적 프로퍼티는 static  키워드를 통해서 정의할 수 있습니다. 


  - 접근법
```js
console.log(Student.Name); //권정열이 출력됨
}
``` 
정적 프로퍼티는 클래스를 통해서 접근할 수 있습니다. <br>
반대로 instance를 생성해서 접근을 시도할 순 없습니다.
		
#### Instance property와 Static property 사용처
- 각 인스턴스가 키나 몸무게 등과 같은 특성을 지녀 개별 인스턴스마다 다른 상태를 표현할 필요가 있는 경우는 인스턴스 프로퍼티를 정의해서 사용하는 것이 좋습니다.
- 반대로 모든 인스턴스가 공유할 필요가 있는 기능 쉽게 예를 들면 모든 인스턴스에 '걷기'라는 기능이 공통적으로 필요하다면 개별적으로 정의하기보다는 정적 프로퍼티로 정해서 일괄적으로 관리하는 것이 좋습니다.

Property와 method의 관계
-	Property는 object를 위해서 데이터를 저장하고
- Method는 object가 요청 받을 수 있는 동작
