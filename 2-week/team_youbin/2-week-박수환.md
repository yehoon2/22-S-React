### 함수

함수 선언문 vs 함수 표현식

함수 선언문

```jsx
function hello(){
	console.log("hello");
}
```

함수 표현식

```jsx
let hello = fuction(){
	console.log("hello")
}
```

함수 선언문은 함수를 어느 위치에서든 호출 가능하다.

함수 표현식은 함수를 생성한 후 호출 가능하다.

화살표 함수

```jsx
let add = (n1,n2)=>{
	let result = n1+n2;
	return result;
};
```

화살표 함수를 사용하면 함수를 보다 간결하게 작성할 수 있다.

화살표 함수는 익명 함수(함수를 재사용 하지 않을 목적으로 함수에 이름을 붙이지 않는 함수)로만 사용 가능 하기 때문에, 함수 표현식으로 쓴다.

화살표 함수는 객체의 메소드, 생성자 함수로는 사용할 수 없다.

화살표 함수의 this는 언제나 상위 스코프의 this를 가리킨다. → 렉시컬 스코프(함수 선언 위치에 따른 상위 스코프 결정)와 유사

### DOM 노드 접근

DOM 노드 접근 방법

- id로 접근
- 태그 이름으로 접근 → HTML Collection 형태로 반환
- 클래스로 접근 → HTML Collection 형태로 반환
- CSS 선택자로 접근
    
    querySelector → 해당 모든 노드 선택(Node Collection 반환)
    
    querySelectorAll → 해당 첫 노드 반환
    
    ```jsx
    // id로 접근
    const a = document.getElementbyId('id');
    // 태그이름으로 접근
    const b = document.getElementByTagName('태그');
    // 클래스로 접근
    const c = document.getElementByCalssName('class');
    // CSS선택자로 접근
    const d = document.querySelector('선택자');
    const e = document.querySelectorAll('선택자');
    ```
    

### 부모, 자식, 형제 노드 접근

부모노드 접근

parentNode → 부모 노드 반환, parentElement → 부모 요소 노드 반환

```jsx
var child;
const a = child.parentNode;
const b = child.parentElement;
```

자식 노드 접근

cihldNode → 자식 노드 반환, children → 자식 요소 노드 반환

```jsx
var parent;
const a = parent.childNode;
const b = parent.chidren;
```

형제 노드 접근

previous/next+Sibling → 앞뒤 형제 노드 반환

previous/next+ElementSibling → 앞뒤 형제 요소 노드 반환


### 노드 생성 추가 복제

**요소 노드 생성** : createElement();

```jsx
const a = document.createElement("태그이름");
```

**노드 추가** : 

appendChild(); → 부모 요소 노드 밑 마지막에 자식 요소 노드 추가

insertBefore(a,b); → 부모 요소 노드 밑 b 전에 a 추가 

기존에 존재하는 노드를 appendChild(), insertBefore()에 사용하면 해당 위치로 변경

```jsx
var parent;
var child1;
var child2;

// 마지막에 child1 추가
parent.appendChild(child1);
// child2 전에 child1 c추가
parent.insertBefore(child2,chil1); 
```

**노드 복제**

cloneNode();

```jsx
var a;
// parameter false(기본)면 겉 요소만 복제, true면 자식 노드까지 모두 복제
const clone_a = a.cloneNode();  
```

**노드 삭제**

removeChild();

### CSS 스타일, Class 제어

**스타일**

요소.style.스타일속성 = ‘ ‘;

```jsx
var a;
a.style.backgroundColor = 'red';
```

**Class 제어**

요소.classList → 해당 요소의 클래스를 리스트 형태로 반환

```jsx
var a;
a.classList.add('color-red');
a.classList.add('color-red', 'bg-blue');
a.classList.remove('color-red');
a.classList.replace('color-red', 'color-yellow');
a.classList.toggle('color-red'); -> // 있으면 제거 없으면 추가
```

### 이벤트 핸들러

**이벤트 핸들러 할당**

- html 태그 속성
- 이벤트 함수 할당
- 이벤트 리스너 ← 추천
    
    일부 이벤트(ex. DOMContentLoaded : 문서 로드 완료 시 발생이벤트)는 이벤트 리스너를 통한 이벤트만 작동
    
    ```jsx
    fucntion sayHi(){
    	alert("hi");
    }
    
    // html태그 속성
    <button onclick="alert('hi')">클릭1</button>
    <button onclick="sayHi()">클릭2</button>
    
    // 이벤트 함수 할당
    var a
    a.onclick = sayHi; // 함수명 뒤에()사용x return값 반환하기 때문
    
    // 이벤트 리스너
    var a
    a.addEventListener("onclick",sayHi);
    a.addEventListener("onclick",() => {
    	alert("hi");
    });
    
    // 할당된 이벤트 리스너 제거
    a.removeEventListener("onclick",() => {
    	alert("hi");
    });
    ```
    
    *핸들러는 event객체를 파라미터로 받는다.
    