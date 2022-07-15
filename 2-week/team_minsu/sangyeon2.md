# DOM

### 1. DOM이란?

**문서 객체 모델**(The Document Object Model, 이하 DOM) 은 HTML, XML 문서의 프로그래밍 interface 이다. 

**문서 객체**란 <html>이나 <body> 같은 html문서의 태그들을 JavaScript가 이용할 수 있는 객체(object)로 만들면 그것을 문서 객체라고 한다.

또한, 웹 페이지를 스크립트 또는 프로그래밍 언어들에서 사용될 수 있게 연결시켜주는 역할
<br><br>


### 2. DOM 구조

![Untitled](https://blog.kakaocdn.net/dn/dIJEVs/btqvMalhNUo/2kKZkghzLiODKqM9WmQekK/img.png)

- Document Node : 최상위에 존재하며 DOM 트리에 접근하기 위한 Root Node
- Element Node : h1, div 같은 태그를 가르키는 Node
- Attribute Node : class, id , href, style 같은 속성에 대한 Node
- Text Node : div Hello World div 에서 태그 안에 감싸진 Hello Wolrd를 가르키는 Node

Root Node 는 부모가 없는 node로, 위에서는 document가 Root Node 이다.

Leaf Node 는 자식이 없는 node로, 위에서는 초록색 Text Node 들이 Leaf Node이다.
<br><br>


### 3. DOM 접근 방식

대표적으로 id 선택자로 접근하는 getElementById()메서드, class값으로 접근하는 getElementByClassName()메서드, 태그이름으로 접근하는 getElementsByTagName()메서드 등이 있다. 그에 관한 기본형과 예시는 아래와 같다.

1. **getElementById() 메서드 기본형** 요소명.getElementById("id명") ex) document.getElementById("heading")
2. **getElementByClassName() 메서드 기본형** 요소명.getElementByClassName("class명") ex) document.getElementByClassName("bright")
3. **getElementsByTagName() 메서드 기본형** 요소명.getElementsByTagName("태그명") ex) document.getElementsByTagName("p")
<br><br><br>

# Event Handdling

[[JS] 이벤트 핸들링과 바인딩, 이벤트 흐름](https://victorydntmd.tistory.com/85)

### 1. Event Handdling이란?

이벤트(event)란 대표적으로 클릭, 키보드 입력 등 사용자의 어떤 행위를 의미합니다.

이러한 이벤트를 처리하는 것을 **이벤트 핸들링**이라고 한다.
<br><br>

### 2. Event Handdling 과정

1. 이벤트를 받아줄 **요소를 선택**한다.
2. 그 요소가 어떤 이벤트에 반응할지, 즉 요소와 이벤트를 연결해주는 **바인딩**을 한다.
3. 이벤트가 발생했을 때 실행될 **코드를 작성**한다.
<br><br>

### 3. 바인딩(Binding)

요소와 이벤트를 연결해주는 바인딩을 하는 방법에는 여러가지가 있다.

**1) HTML 이벤트 핸들러**

HTML 요소의 onclick 속성에 JS 함수를 호출하여 바인딩하는 방법

```html
<button class="btn" onclick="myFunction()">
```

**2) DOM 이벤트 핸들러**

DOM 요소에 이벤트를 바인딩하고 이벤트가 발생하면 실행될 코드를 함수로 작성하는 방법

```jsx
element.on이벤트이름 = myFunction(){...}
```

**3) Dom 이벤트 리스너**

DOM 요소에 addEventListener 메서드를 호출하여 이벤트를 바인딩하고 수행할 함수를 작성

```jsx
element.addEventListener("이벤트이름", myfunction(){ ... }, [, boolean]);
```

바닐라 JS 기준으로 가장 많이 사용되는 방식
<br><br>

### 4.이벤트 흐름 - **Event Bubbling, Event Chapturing**

- **Event Bubbling**

DOM 구조에서 최상위 요소는 document이고 그 아래에 head , body , a , ul , li 등이 있는 구조 즉, 트리구조로 되어 있다.

그래서 어떤 요소에 대해 어떤 이벤트가 발생하면, 그 요소의 부모도 같은 이벤트의 영향을 받게된다.이러한 이벤트 흐름을 **Event Bubbling**이라고 한다.

```jsx
<ul id="a">
    <li id="b">
        <button id="c">alert 발생</a>
    </li>
</ul>

<script>
    function showElement() {
        alert(this.innerHTML);
    }
    el = document.getElementById("a");
    el.addEventListener('click', showElement, false);

    el = document.getElementById("b");
    el.addEventListener('click', showElement, false);

    el = document.getElementById("c");
    el.addEventListener('click', showElement, false);
</script>
```

위의 예제는 id 속성 값 a, b, c에 대해 click 이벤트를 바인딩했을 때, a, b, c 중 어느 요소를 클릭하느냐에 따라 alert 창이 몇 번 발생하는지를 보여준다.

C 클릭시 : 이벤트 버블링이 되어 b,a도 클릭되어 총 3번의 alert 창이 발생

B 클릭시 : 이벤트 버블링이 되어 a도 클릭되어 총 2번의 alert 창이 발생

A 클릭시 : 1번의 alert 창이 발생

- **Event Capturing**

Event Capturing은 자식으로 이벤트가 연계되는 이벤트 흐름을 말한다. 즉, Event Bubbling의 반대 개념이다.

- **Dom 이벤트 리스너**

```jsx
element.addEventListener("이벤트이름", myfunction(){ ... }, [, boolean]);
```

이 부분에서 마지막 boolean 부분에

**False를 넣을 시** : Event Bubbling 발생

**True를 넣을 시** : Evnet Capturing 발생
<br><br><br>

# ES6 문법

[[JavaScript] ES6 문법 - 하나몬](https://hanamon.kr/javascript-es6-%EB%AC%B8%EB%B2%95/)

### 1. ES란

ES란, ECMAScript의 약자이며 자바스크립트의 표준, 규격을 나타내는 용어이다.뒤에 숫자는 버전을 뜻하고 `ES5`는 2009년 `ES6`는 2015년에 출시되었다.
<br><br>

### 2. 변경된 점

1. **let, const 키워드**
- 블로스코프를 가지고 재선언 불가 재할당 가능한 **let 변수** 선언 키워드와 상수 선언 키원드 **const**가 추가되었다.
- 기존 var 키워드만 있었을 때 보다 예측 가능한 코드를 작성 할 수 있게 되었다.
<br><br>

2. ****템플릿 리터럴****
- 사용법은 “(back tick)으로 가능하다.
- ${} 중괄호 앞에 달러 표시를 통해 자바스크립트 표현식 사용이 가능하다.

```jsx
// ES5
var str1 = ', ';
var str2 = 'World!';
var str3 = 'Hello' + str1 + str2;
// ES6
let str1 = ', ';
let str2 = 'World!';
let str3 = `Hello ${str1} ${str2}`;
```
<br><br>

3. ****객체 리터럴****
- 전체적으로 훨씬 간결해진 코드로 객체를 선언할 수 있다.
- 속성명과 속성값의 변수명이 같다면, 하나만 기입가능

```jsx
// ES5
var myName = 'cucuhama';
var obj = {
	myOld : '23',
    myLocation : 'GangNam',
    myName : myName  		// 여기서 myName이라는 속성명(key값)의 값(value값)으로 변수 myName을 지정했습니다.   
}
// ES6
const myName = 'cucuhama';
const obj = {
	myName,				// 이렇게 한번만 적어도 myName : myName 처럼 동작합니다.
    myOld : '23',
}
```

- 메서드 속성을 정의할 때 function() 키워드 생략가능

```jsx
// ES5 기존 문법
var obj = {
	prop1 : "something",
    prop1 : "anything",
    method1 : function(){					// 반드시 메서드일 경우 function() 키워드 필요
    	console.log("이것은 메소드입니다");
    },
};

// ES6
const obj = {
	porp1 : "somethind",
    prop2 : "else",
    method1() {								// 바로 함수명을 적으면 됩니다.
    	console.log("이것은 메서드입니다.");
    }
 };
```

- 동적 속성명을 바로 정의 가능

```jsx
// ES5 에서 동적 속성명 하기

// 우선 먼저 객체를 정의하고
var obj = {
	prop1 : "lulu",
    prop2 : "lala",
    method1 : function(){
    	console.log("룰루 랄라");
    },
};
 
// 객체를 먼저 생성하고 그 다음에 동적 속성명을 정의한다.
var value = "prop3";
obj[value] = '동적이군';   // obj에 prop3이란 속성이 생기고 값으로 "동적이군"이 들어간다.

// ES6
let value = "prop3";			// 동적으로 정의할 속성명을 변수 "value"에다가 저장합니다. 
const obj = {
	prop1 : "룰루",
    prop2 : "랄라",
    hoho() {
    	console.log("호호 함수");
    },
    [value] : '동적이군',		// 이렇게 바로 객체리터럴에서 동적으로 정의할 수 있습니다.
};
```
<br><br>

4. ****화살표 함수****
- 함수 표현식을 화살표 함수로 표현할 수도 있다.
- 화살표 함수가 추가되어 함수를 간결하게 나타낼 수 있게 되어 가독성 및 유지 보수성이 올라갔다.
- 만약 함수의 본문(body)에 return만 있는 경우 화살표 함수는 return과 {}를 생략할 수 있다. 단, 같이 생략해야한다.
- return문에서 소괄호는 사용가능하다.

```jsx
// ES5
function plusFn(a, b) { 
  return a + b; 
} 
// ES6
// 함수 표현식 - 화살표 함수
const plusFn = (a, b) => {
  return a + b;
}
// 함수 표현식 - 화살표 함수 (생략형)
const plusFn = (a, b) => a + b;
```
<br><br>

5. ****구조 분해 할당****
- **구조 분해 할당**
 구문은 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 것이다.

```jsx
const obj = {
 firstName: '하나',
 lastName: '몬'
};
const { firstName, lastName } = obj;
firstName // 하나
lastName // 몬
```
<br><br>

6. ****Promise****
- 자바스크립트에서 비동기 처리를 기존에는 콜백 함수를 사용한, 콜백 패턴을 사용하였다.
- 결과론적으로, 콜백헬을 발생시켰다.
- 이를 해결하기 위해 프로미스가 도입되었고, 프로미스 후속처리 메소드를 이용해 에러 처리를 효과적으로 할 수 있게 되었다.
<br><br>

7. **Class**
- 자바스크립트는 프로토타입 기반의 객체 지향 언어이다.
- 클래스 기반의 객체 지향 프로그래밍도 할 수 있게 Class 키워드를 도입하였다.
- 자바스크립트에서 클래스는 내부적으로 프로토타입을 이용해서 만들어졌다.
- 클래스는 호이스팅이 `let`, `const` 키워드 처럼 동작한다.
<br><br>

8. **String Method(includes, startsWith, endsWith)**
- 포함되어있는지(includes), 시작하는지(startsWith), 끝나는지(endsWith)
- boolean 타입을 return 해준다.

```jsx
const str = 'Hello World Hanamon';
str.includes("Hana"); // true
str.startsWith("Hello"); // true
str.endsWith("mon"); // true
```
<br><br>

9. ****Multi-line String****
- 문자열이 라인을 넘어가게 되면 ‘\n’ 과 덧셈 연산자를 사용했어야했다.
- 백틱을 사용하게 되면서 여러줄의 문자열 관리도 편해졌다.

```jsx
// ES5
var str = 'asdhasfhfsahsfhfshasfhsfahsfahsfahasfh.\n' + 
'mxmxmxmxmxmxmxmmxmxmxmxmxmmxmxmxmxmxm.\n'
// ES6
let str = `asdhasfhfsahsfhfshasfhsfahsfahsfahasfh
mxmxmxmxmxmxmxmmxmxmxmxmxmmxmxmxmxmxm`;
```
<br><br>

10. ****Default Parameter****
- 함수에 인자를 넘겨줄 때, default parameter 설정이 가능함
- 따라서 함수 실행시, 별도로 인자를 넘기지 않을 경우, deafult로 지정된 값이 넘어가도록 작동함

```jsx
const func = (a, b = "b", c = "c") => {
  console.log(a, b, c);
};

func("a");
//a b c
```

### 호이스팅

인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것

- `var`로 선언한 변수의 경우 호이스팅 시 `undefined` 로 변수를 초기화
- `let`과 `const`로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않음

```jsx
catName("클로이");

function catName(name) {
  console.log("제 고양이의 이름은 " + name + "입니다");
}

/*
결과: "제 고양이의 이름은 클로이입니다"
*/
```

```jsx
console.log(num); // 호이스팅한 var 선언으로 인해 undefined 출력
var num; // 선언
num = 6; // 초기화
```
<br><br><br>

# Callback, Promise, Acync-Await
## CallBack

[콜백이란 무엇인가](https://medium.com/@flqjsl/%EC%BD%9C%EB%B0%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-56c26e1f1bc3)

### 1. callback 이란?

함수가 끝나고 난 뒤에 실행되는 함수.

함수는 함수를 인자로 받고 다른 함수를 통해 반환될 수 있다. 인자로 대입되는 함수를 **콜백함수**라고 부른다.

대표적인 콜백함수 예시 (setTimeout)

```jsx
function fn_newCallBack(){
  console.log("비동기적으로 호출되고 싶다.");
}

console.log("-------  호출 직전 -------");

setTimeout(fn_newCallBack, 3 * 1000); // 3초 뒤 콜백 호출

console.log("-------  호출 이후 -------");
```

```jsx
-------  호출 직전 -------
-------  호출 이후 -------
비동기적으로 호출되고 싶다.
```
<br><br>

### 2. 콜백 지옥

함수의 매개 변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상을 말한다.

```jsx
step1(function (value1) {
    step2(function (value2) {
        step3(function (value3) {
            step4(function (value4) {
                step5(function (value5) {
                    step6(function (value6) {
                        // Do something with value6
                    });
                });
            });
        });
    });
});
```
<br><br>

## Promise

[콜백지옥해결 Promise, async / await](https://velog.io/@5o_hyun/%EC%BD%9C%EB%B0%B1%EC%A7%80%EC%98%A5%ED%95%B4%EA%B2%B0-Promise-async-await)

### 1. Promise란  

Promise는 콜백지옥을 해결하기 위한 방법 중 하나이다.

Promise는 다음 중 하나의 상태를 가진다.

- 대기 ( pending ) : 이행하지도 거부하지도 않은 초기 상태
- 이행 ( fulfill ) : 연산 성공
- 거부 ( reject ) : 연산 실패

![Untitled](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/promises.png)

기본적으로 `pending`상태에서,

- 비동기 처리 성공 : `resolve`함수를 호출해 promise를 `fulfilled`상태로 변경
- 비동기 처리 실패 : `reject`함수를 호출해 promise를 `rejected`상태로 변경

pending상태에서 fulfilled 혹은 reject상태로 변경되면 settled상태가 된다.

### 2. Promise의 후속 처리 method
1. then
- then 메소드는 두 개의 콜백 함수를 인자로 전달 받음
- 첫 번째 콜백 함수는 성공(fulfilled, resolve 함수가 호출된 경우)시에 실행
- 두 번째 콜백 함수는 실패(rejected, reject 함수가 호출된 경우)시에 실행
- then 메소드는 기본적으로 프로미스를 반환한다.

```jsx
const promise = () => new Promise((resolve, reject) => {
    let a = 1 + 1

    if(a == 3) {
        resolve('success')
    } else {
        reject('failed')
    }
})

promise().then((message) => {
    console.log('This is in the then ' +  message)
}, (error) => {
    console.log('This is in the then ' +  error)
})
```

```jsx
This is in the then failed
```

1. catch
- catch 메소드는 비동기 처리 혹은 then 메소드 실행 중 발생한 에러(예외)가 발생하면 호출
- catch 메소드 역시 프로미스를 반환한다.

```jsx
const promise = () => new Promise((resolve, reject) => {
    let a = 1 + 1

    if(a == 3) {
        resolve('success')
    } else {
        reject('failed')
    }
})

promise().then((message) => {
    console.log('This is in the then ' +  message)
}).catch((error) => {
    console.log('This is in the catch ' + error)
})
```

```jsx
This is in the then failed
```
