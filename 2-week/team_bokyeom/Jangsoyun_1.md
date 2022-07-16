# var / let / const

> 목차
> 
1. `var` `let` `const` 특징
2. `hoisting`
3. `scope`

---

> **var**
> 
- 중복선언이 가능하다.

```jsx
var a=3;
console.log(a);

var a=12;
console.log(a);
```

- 결과
    
    
    | 3 |
    | --- |
    | 12 |
    
- 재할당이 가능하다.

```jsx
var a=3;
console.log(a);

a=12;
console.log(a);
```

- 결과
    
    
    | 3 |
    | --- |
    | 12 |
    

> **let**
> 
- 중복 선언이 불가능하다.

```jsx
let a=3;
console.log(a);

let a=12;
console.log(a);
```

- 결과
    
    
    | “error” |
    | --- |
    

- 재할당이 가능하다.

```jsx
let a=3;
console.log(a);

a=12;
console.log(a);
```

- 결과
    
    
    | 3 |
    | --- |
    | 12 |
    

> **const**
> 
- 중복 선언, 재할당 모두 불가능하다.

```jsx
const a=3;
console.log(a);

const a=12;
console.log(a);
```

- 결과
    
    
    | “error” |
    | --- |
    

```jsx
const a=3;
console.log(a);

a=12;
console.log(a);
```

- 결과
    
    
    | “error” |
    | --- |
    

```jsx
const a=3;
console.log(a);

const b=12;
console.log(b);
```

- 결과
    
    
    | 3 |
    | --- |
    | 12 |
    

---

> **scope**
> 

javascript에는 `전역 스코프(global)` 과 `지역 스코프(local)` 가 있다.

```jsx
var a=10;
function myPrintf(){
	var a=14;
	console.log(a);
}
myPrintf();
console.log(a);
```

- 결과
    
    
    | 14 |
    | --- |
    | 10 |
    

`전역 스코프(global)`

어느 곳에서든지 해당 변수에 접근할 수 있다.

`지역 스코프(local)`

해당 지역에서만 접근할 수 있다. 

지역 스코프에는 `블록 스코프`와 `함수 스코프`가 있다.

`블록 스코프` **let, const**

`함수 스코프` **var**

```jsx
var a=3;
{
  var c=a;
  console.log(c);
}
```

> **hoisting**
> 

호이스팅이란 스코프 내의 선언들을 상단부에 끌어올려주는 것 같은 현상이며, 자바스크립트의 모든 선언에서 발생한다.

```jsx
console.log(a);
var a=12;
```

- 결과
    
    
    | undefined |
    | --- |
    
    호이스팅이 일어나서 에러는 안 떴지만, undefined 라고 나왔다. var 의 초기값은 undefined이기 때문이다.
    

```jsx
console.log(a);
const a=12;
```

- 결과
    
    
    | “ReferenceError” |
    | --- |
    
    참조 에러가 났다. 선언은 끌어 올렸는데, const의 초기값이 없어서이다. 
    

따라서 호이스팅은 선언만 끌어올리고, 초기화작업은 끌어올려주지 않는다.

# Callback / Promise / Acync-Await

TMI)

 Acync를 어떻게 발음하는지 궁금해서 검색해봤는데 “에이싱크”라고 하네요. 

Acync 외에도 다른 용어들 발음 쫙 모아놓은 문서를 발견했습니다 ㅎㅎ

재미삼아 읽어보세영

[https://docs.google.com/spreadsheets/d/17pLAxtVJBY3SMxPPe1AIfWh0kEu2zAgB4H5w_-LezUM/edit#gid=0](https://docs.google.com/spreadsheets/d/17pLAxtVJBY3SMxPPe1AIfWh0kEu2zAgB4H5w_-LezUM/edit#gid=0)

**Callback**

콜백이란 다른 함수의 전달인자로 쓰이는 함수를 말한다.

```jsx
function A(callback){
	callback();
}

function B(){
	console.log('콜백: 절 부르셨나요?');
}

A(B);
```

- 결과
    
    
    | “콜백: 절 부르셨나요?” |
    | --- |

이걸 굳이 콜백이라고 정의하고 쓸 필요가 있나 싶어서 어떨 때 쓰는지 찾아봤습니다.

1) 반복 실행(iterater)

2) event handler(DOM에서 이벤트)

3) 동기/비동기 함수 제어

그렇다고 합니다.

아래는 글을 읽다가 모르는것이 생겨 찾아보고 정리한 내용입니다.  ES6문법이라네요.

- 화살표함수
    
    ```jsx
    //함수
    function myFunction(a,b){
    	return a+b;
    }
    
    //화살표함수
    const myFunction=(a,b) =>{
    	return a+b;
    }
    ```
    
- 구조분해 할당
    
    구조분해 할당은 값을 해체한 후, 각 값을 변수에 새로 할당하는 것이다. 객체나 배열에 사용한다.
    
    ```jsx
    const arr=['장','소윤'];
    const [ firstName, secondName]=arr;
    console.log('성: '+ firstName );
    console.log('이름: '+secondName );
    
    ```
    
    결과
    
    | 성: 장 |
    | --- |
    | 이름: 소윤 |

죄송합니다 여기서부터는 진짜 모르겠어요 다시 공부해올게요..

**Promise**

비동기 함수 전달 패턴을 사용하다가 콜백헬(무지성 들여쓰기)이 발생해서 도입된것이다.

**Acync-Await**

비동기 콜백에서 promise랑 연관되는.. 어쩌구인거같습니다.