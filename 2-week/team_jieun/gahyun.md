# JavaScript

- DOM
    - DOM이란?
    
    웹  문서를 접근하고 제어하기 위해 웹 문서를 객체화 한 것
    
    웹 문서를 객체화 함으로써 객체로 웹 문서를 제어하는 것
    
    ex) document.querySelector(’body’);
    
    - 트리구조와 노드
    
    document안에는 head와 body body안에는 div span 등등 이런 트리 구조로 이루어졌다
    
- 숫자와 문자(데이터 타입)
    - 숫자
    
           정수와 실수를 엄격하게 구분하지 않음 
    
           Infinity : 양수를 0으로 나누는 경우 , -Infinity : 음수를 0으로 나눈 경우
    
           NaN: 숫자가 아닌 값을 나누는 경우
    
    - 문자 작성
    
          큰 따옴표 , 작은 따옴표를 통해 문자의 시작을 알림
    
          정보안에 따옴표를 쓰고 싶으면 ? “에서는 ‘로 ‘에서는 “로
    
          or 역슬래시하고 따옴표 사용
    
          문자열들의 결합은 ‘+’를 사용해서 썼지만  백틱이라는 문법으로
    
           ex) let name=’박가현’ console.log(’내이름은 {$name} 입니다’);가능
    
    - 문자와 관련된 속성/문법
    
           줄바꿈 :  역슬래시 사용
    
           typeof : 변수 타입 알기
    
           문자열.length: 문자열 길이 알기
    
           더 다양한 것은 [https://opentutorials.org/course/50](https://opentutorials.org/course/50)
    
    - Symbol
    
    ES6에서 도입한 새 데이터 타입(자주 쓰이는 건 아닐걸 ..?) 
    
    다른 식별자와 혼동해서는 안되는 고유한 식별자가 필요할 때 
    
    항상 유일한 값 
    
    ex) const a =Symbol(’가나다’);
    
         const b=Symbol(’가나다’);
    
    이 둘은 내용도 같고 데이터 타입도 같지만 Symbol로 인해서 서로 다르다고 출력이 됨
    
    실제로 어디서 많이 쓰이는 지는 모르겠음
    
    - null과 undefined
    
    둘다 값이 비어있는 상태지만 null은 값이 없는 상태 undefined는 값이 할당되지 않은 상태
    
    프로그래머의 의도 차이로도 볼 수 있음
    
- 변수와 상수
    - let 예약어
    
    예약어: 프로그래밍 문법으로 사용하고 있는 키워드
    
    let : 변수를 선언할 때 쓰이는 예약어
    
    (자바와 다르게 문자열 숫자 모두 담을 수 있음)
    
    - const
    
    상수를 할당받는 예약어
    
    상수도 변수와 마찬가지로 값을 할당 받을 수 있지만 한번 할당한 값을 바꿀 수는 없음
    
    선언과 동시에 할당이 이루어짐
    
    ? : 프로그래밍시 성능에서 이점을 얻기 위해 let보다 const를 사용하면 더 좋다는데 그 이유는 ?
    
    네이밍을 적절히 사용하면 const가 let보다 유지보수와 가독성 향상
    
    객체 내용이 변경되더라도 (속성 변경) 객체 타입 변수에 할당된 주소값은 변경되지 않기에
    
    객체 타입 변수에는 const를 사용하는 것이 좋다
    
    변수 선언에는 기본적으로 const를 사용하고 let은 재할당이 필요한 경우에 사용
    
    [https://poiemaweb.com/es6-block-scope](https://poiemaweb.com/es6-block-scope)
    
    - 전역스코프 변수
    
    말그대로 전역변수 
    
    - 블록스코프 변수
    
    블록 {} 묶인 영역이 블록 스코프이며 블록 안에 선언된 변수는 블록 안에서만 접근 가능
    
    - 식별자 이름
    
    글자 달러기호 밑줄(_)로 시작해야하고 글자 숫자 달러기호 밑줄만 쓸 수 있음
    
    예약어는 사용 못함 ( let const function for if ……)
    
    식별자 이름을 지을 때는 명사로 짓기
    
    - var이 안 좋은 이유
    
    선언을 여러번 할 수 있다 ex) var k =30 ; var k=3;도 가능
    
    선언 전에 사용할 수 있다 ex) k=30; var k; 가능
    
    스코프에 영향을 받지 않는다 즉 블록 레벨 스코프를 따르지 않고 모두가 전역 변수임
    
    - 호이스팅
    
    코드가 실행 되기 전 변수나 함수의 선언이 자바스크립트 파일의 최상단으로 끌어 올려지는 것
    
    var과 function으로 선언된 변수 함수만 호이스팅이 발생 (그래서 선언 전에 사용 가능한것 같음)
    
    ex) hello();  function hello(){}이게 가능
    
    let const class를 이용한 선언은 호이스팅되면 에러
    
    [https://poiemaweb.com/es6-block-scope](https://poiemaweb.com/es6-block-scope)
    
    - ‘use strict’
    
    Strict Mode로 이런 말도 안되는 현상과 에러를 막기 위해 생김
    
    ex)암시적 전역 변수 등등
    
    [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode)
    
    [https://beomy.tistory.com/13](https://beomy.tistory.com/13)
    
- 연산자
    - ===
    
    ==는 데이터 타입이 달라도 내용만 같으면 true를 출력하는데
    
    ===는 내용이 같더라도 데이터 타입까지 같아야 true를 출력
    
    결론 : ===사용하자
    
    - ! = =
    
    같지 않은걸 데이터 타입까지 비교함 위랑 같이
    
    ! = 대신 ! = = 사용
    
    - 단축평가
    
    and 연산자 중에 하나라도 false면 나머지 피연산자는 평가를 안함
    
    이거를 생각 못하다가 오류 날 수도 있으니까 주의
    
- 제어문
    - 조건문
    
    if , else , else if.. ~~
    
    자바 스크립트는 유연한 언어이기에  존재하는 변수를 조건에 넣어도 실행 가능
    
    es) let a=3; if (a) {    } 가능
    
    - 거짓같은 값
    
    얘네는 false로 취급해서 위와 같은 기능을 못함
    
    false, 0 , -0 , 0n , “” ,null , undefined ,  NaN
    
    - for in
    
     for문 객체에 있는 키 항목들을 반복적으로 반환
    
    ex)   const person={ name : ‘가나다’ age:20 job =’개발자’} 
    
    for(let key in person){ console.log( person[key] );  console.log(key ); }
    
    여기서 key는 프로퍼티를 반환하고 person[ key ] 는 프로퍼티 값을 반환
    
    객체에 많이 쓰임
    
    - for of
    
    배열 같은 객체에서 반복해서 값을 하나씩 반환 
    
    for( let value of array ){  console.log( value ); }
    
    배열에 많이 쓰임
    
    - 쓰이는 제어문
    
    while , for, continue , break , do while , switch
    
- 함수
    - 함수 선언식
    
    함수예약어 , 함수이름 , 함수블록으로 이루어졌고 
    
    이런 식으로 작성하면 호이스팅의 영향을 받음
    
    function hello(){};
    
    - 함수 표현식
    
    예약어 함수이름 =함수 예약어(){}로 이루어졌고
    
    이런 식으로 작성하면 호이스팅의 영향을 받지 않음
    
    ex) let sayHello = function(){} ;
    
    - 익명 함수
    
    function(){} 이런식으로 된거 이름이 없어서 익명함수
    
    - 즉시 실행 함수
    
    (function( ){ ……….  })();
    
    만들자마자 즉시 실행 
    
    - 파라미터 기본 값
    
    전달을 받지 못한 매개변수는 undefined로 정의됨 이걸 막기위해서
    
    function sum(number=0 ,number1=0){   return number1+number;   } 이런식으로 정의
    
    이렇게 되면 number가 값을 할당 받지 못했을 때 0으로 정의됨
    
    값을 할당 받았을 땐 그대로 그 값을 적용
    
    - ArrowFunction
    
    function 예약어 생략 가능
    
    익명 함수로만 사용할 수 있다 그래서 함수 표현식을 사용한다
    
    함수 매개변수가 단 하나면 괄호 생략 가능
    
    함수 바디가 표현식이 하나면 중괄호와 return 생략 가능
    
    ex) const  f1 name(이제 name인 매개변수) = > ‘hello’ ;
    
         const f3 = function(a,b) { return a+b ;  }
    
         const f4= (a , b) ⇒ a+b;
    
    - 함수 특징
    
    Javascript의 함수는 일급 객체이므로 javascript의 함수는 흡사 변수와 같이 사용될 수도 있다
    
    하지만 다른 객체들과 달리 호출할 수 있다는 특징이 있다
    
    또한 함수도 객체이기에 함수도 프로퍼티를 가질 수 있다
    
    - arguments 프로퍼티
    
    정의 : 함수 호출 시 전달된 인수들의 정보를 담고 있는 순회가능한 유사배열객체
    
    (유사 배열이기에 실질 적으로 배열 메소드 사용하면 에러)
    
    함수 호출할 때 인수들과 함께 arguments 객체가 함수 내부로 전달돼서 
    
    그 값들을 arguments가 가지고 있다
    
    매개변수 갯수가 확정되지 않은 가변 인자 함수 구현때 유용
    
    ```jsx
    function sum(){
    let res=0;
    for(let i=0;i<arguments.length;i++){
    res+=arguments[i];
    }
    return res;
    }
    
    console.log(sum()); //0
    console.log(sum(1,2)); //3
    console.log(sum(1,2,3)); //6
    ```
    
    - caller 프로퍼티
    
    자신을 호출한 함수를 의미
    
    - length 프로퍼티
    
    함수 정의시 작성된 매개변수 갯수를 의미
    
    arguments.length는 호출시 인자의 갯수고 length는 매개변수 갯수니까 값이 다를 수 있다 
    
    ```jsx
    function foo(x,y){
    console.log(foo.length); //2
    }
    ```
    
    - name 프로퍼티
    
    함수명을 나타낸다
    
    - 내부 함수
    
    내부 함수는 자신을 포함하고 있는 부모함수 parent의 변수에 접근 가능하지만 부모 함수는 자식 함수의 변수에 접근 불가
    
- 배열
    - 배열 리터럴 표기법
    
    현업에서 많이 사용
    
    ```jsx
    const job =['의사' , '개발자', '교수'];
    ```
    
    - 배열 생성자 표기법
    
    ```jsx
    const job = new Array('의사','개발자', '교수');
    ```
    
    - 배열 API ( 배열 메서드)
    
    length - 배열 길이를 가져오는 문법
    
    ```jsx
    const job=['의사' ,'개발자','교수'];
    for(int i=0;i<job.length;i++){
    console.log(job[i]);
    }
    ```
    
    push - 배열 끝에 항목을 추가하는 것
    
    ```jsx
    job.push('운동선수');
    ```
    
    forEach - 배열의 항목을 순환하며 처리하기 
    
    오직 Array 객체에서만 사용 가능
    
    foreach의 구문의  인자로callback 함수를 등록할 수 있고 배열의 각 요소들이 반보될 때 call back 함수 호출 →콜백 함수 배울 때 다시
    
    ```jsx
    
    ```
    
    pop - 배열 끝에 항목 제거하기 
    
    ```jsx
    job.pop();
    console.log(job); // 의사와 개발자가 출력
    ```
    
    shift - 배열 앞에 항목 제거하기 
    
    ```jsx
    job.shift();
    console.log(job); // 개발자와 교수가 출력
    ```
    
    unshift - 배열 앞에 항목 추가하기 
    
    ```jsx
    job.unshift('운동선수');
    console.log(job); // 운동선수 의사 개발자 교수 출력
    ```
    
    indexOf - 배열 안 항목의 인덱스 찾기 
    
    ```jsx
    const index =job.indexOf('개발자');
    console.log(index); //의사 개발자 교수 이 순이기에 1이 출력
    ```
    
    splice 
    
    ```jsx
    fruits.splice(1,2); //인덱스 1번부터 2개 제거하겠다는 뜻
    ```
    
    - 구조분해할당
    
    배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담는 것
    
    ```jsx
    const job =['의사','개발자','교수'];
    const [doc , cod , prof]=job;
    console.log(doc); //의사 출력
    
    const [doc , ...others]=job;
    console.log(doc); //의사 출력
    console.log(others); //개발자 교수 출력
    ```
    
    - Spread syntax
    
    …배열이름은 배열 할당 값들을 펼친 것이다 
    
    ```jsx
    console.log(job); //Array(3) 이런 식으로 배열의 전체적 정보들과 값이 나온다면
    console.log(...job); //애는 딱 배열의 값들 정보들만 다룸
    ```
    
    - 배열 복사하기
    
    배열은 참조값을 갖고 있기에 다른 변수들과 달리 배열을 변경하면 할당 받은 다른 배열도
    
    함께 변경이 된다 
    
    ```jsx
    const fruits = ['오렌지 ' , '포도' , '사과'];
    const copy=fruits;
    ```
    
    이런 식이면 copy나 fruits 가 변경될 때 나머지 하나도 함께 변경이 된다
    
    그래서 배열 복사를 위해 
    
    ```jsx
    const copy=[...fruits]; // 항목 값들을 펼치는 거
    const copy=Array.from(fruits);
    const copy=fruits.slice;
    //이런 식으로 해야함
    ```
    
- 객체
    - 객체의 정의와 구성
        
        객체는 키와 값으로 구성된 프로퍼티들의 집합
        
        객체는 데이터(프로퍼티)와 그 데이터에 관련되는 동작(메소드)들을 모두 포함해 구조화하는데 유용
        
        (메소드는 객체에 제한되어 있는 함수)
        
    - 객체의 생성
    
    **객체 리터럴** : 중괄호를 사용해서 객체를 생성하는 가장 일반적인 방법.
    
    ```jsx
    let person ={
    name: '가현',
    gender : 'female',
    sayhello:function(){
    console.log('Myname is  {$this.name}');
    }
    }
    ```
    
    **객체 생성자 문법** : object를 사용해서 객체를 생성
    
    object 생성자 함수를 호출하여 빈 객체를 생성한 후 프로퍼티 또는 메소드를 추가하는 법
    
    ```jsx
    let person = new object();
    person.name='가현';
    person.sayhello= function(){
    console.log('Myname is  {$this.name}');
    }
    ```
    
    **생성자 함수** : 마치 객체를 생성하기 위한 템플릿 ( 클래스) 처럼 사용해서 프로퍼티가 동일한 객체 여러 개를 간편하게 생성할 수 있다
    
    ```jsx
    function Person(name , gender){
    this.name = name;
    this.gender = gender;
    this.sayHello=function(){}
    }
    ```
    
    <aside>
    💡 **this** 는 생성자 함수가 생성할 인스턴스를 가르킵니다. this에 연결된 프로퍼티와 메소드는 **외부에서도 참조가 가능하지만** this가 아닌 일반 변수는 **private으로 생성자 함수 내부**에서만 접근 가능하다 !
    
    </aside>
    
    - 객체 프로퍼티 동적으로 생성 및 제거
    
    프로퍼티 생성 
    
    프로퍼티 제거 delete 연산자를 통해 제거
    
    ```jsx
    person.hobby='코딩'; //프로퍼티 생성
    
    delete person.hobby; //프로퍼티 삭제
    ```
    
    javascript는 동적 언어여서 그런 게 가능
    
    - Spread operator
    
    객체 안의 프로퍼티를 펼치는 방식으로 …표기법을 사용하여 사용할 수 있음
    
    - 객체 복사
    
    객체는 참조 타입으로쉽게 복사되지 않음
    
    Spread operator를 이용한 복사
    
    object.assign()을 이용한 복사
    
    ```jsx
    let animal ={...people};
    
    const obj1 - Object.assign({}, people);
    ```
    
- 클래스
    - 클래스의 정의
    
    자바스크립트의 객체를 생성하기 위한 것
    
    생성자 함수를 클래스로 정의 가능
    
    ```jsx
    Class Person{
    constructor (name){
    this.name=name;}
    sayHi(){
    console.log('hi');}
    }
    const p1 = new Person('gahyun');
    ```
    
    - 표현식으로 정의한 클래스
    
    ```jsx
    const foo = class Myclass{};
    const f1= new foo();
    //이때 Myclass 이름은 사용 불가
    ```
    
    - 인스턴스 생성
    
    new 연산자와 함께
    
    new 연산자를 사용하지 않고 constructor를 호출하면 에러
    
    - Constructor
    
    인스턴스 생성과 동시에 클래스 필드의 생성과 초기화를 실행한다
    
    <aside>
    💡 생성자는 클래스 내에 한개만 존재할 수 있음 ! 생략도 가능
    
    </aside>
    
    - 클래스 필드
    
    ~~클래스 바디에 클래스 필드를 선언하면 문법 에러가 남~~
    
    2019년 이후로 클래스 바디에 클래스 필드를 선언해도 된다.
    
    클래스 필드의 선언과 초기화는 반드시 생성자 내부에서 !
    
    즉 클래스 바디에는 메소드만 선언 가능
    
    또한 클래스 필드는 인스턴스를 가르키는 this에 연결
    
    왜? → 외부에서 참조하도록 언제나 public
    
    - 정적 메소드
    
    인스턴스를 생성하지 않아도 호출할 수 있는 메서드
    
    이 메서드 안에서는 this를 사용할 수 없다
    
    일반 메서드 내부에서 this는 클래스의 인스턴스를 가르키기에
    
    인스턴스 생성 없이 this로 하는 것을 불가하다
    
    - 클래스 상속
    
    extends 키워드를 사용하여 클래스 상속
    
    오버라이딩 가능 (상위 클래스가 가지고 있는 메소드를 하위클래스가 재정의)
    
    오버로딩은 지원하지 않지만 arguments를 사용해서 구현 가능
    
    - super 키워드
    
    부모 클래스를 참조하거나 부모 클래스의 constructor를 호출할 때 사용
    
    자식 클래스의 constructor에서 super()를 호출하지 않으면 this에 대한 참조 에러
    
- 정규표현식
    - 정규표현식 정의
    
    문자열에서 특정 내용을 찾거나 대체 또는 발췌하는데 사용
    
    즉 특정한 규칙을 가진 문자열의 집합
    
    사용 예시 ) 입력 받은 비밀번호가 유효한지 체크할 때  , 이메일 유효성 검사할때
    
    - 정규 표현식 리터럴
    
    
    
    - 패턴
    
    패턴에는 검색하고 싶은 문자열 지정
    
    $ 문자열의 끝을 의미
    

    
    - 검색 패턴
    

    
    - 갯수 수량 패턴
    
    
    - 플래그
    

    
    - 정규 표현식 주요 메서드
    

    - 사용 예시
    
    ```jsx
    const url = 'http://example.com';
    //http로 시작하는지 검사하는 패턴
    const regexr = /^http/;  
    
    console.log(regexr.test(url));
    //http로 시작하는 문자열이기에 true 반환
    ```
    
    ```jsx
    const id = 'abc123';
    
    //알파벳 대소문자 또는 숫자로 시작하고 끝나며
    //4~10자리인지 검사
    const regexr = /^[A-Za-z0-9]{4,10}$/;
    ```
    
    - 자료
    
    [https://poiemaweb.com/js-regexp](https://poiemaweb.com/js-regexp)
    
    [https://www.nextree.co.kr/p4327/](https://www.nextree.co.kr/p4327/)
    
    [https://curryyou.tistory.com/234](https://curryyou.tistory.com/234)
    
- this
    - this의 정의
    
    대부분의 this의 경우 함수를 호출한 방법에 의해 결정
    
    this는 호출한 것으로 보면 편함
    
    화살표 함수와 StrictMode에서는 this가 달라지는 예외가 있음
    
    - 전역 스코프에서 this
    
    window객체를 가르킴
    
    - bind 함수
    
    this를 설정할 수 있음
    
    bind는 한번만 가능
    
    ```jsx
    function print(){
    console.log(this);}
    
    let person1= {fullname:'홍길동'};
    
    let bindPrint = print.bind(person1);
    //person1 객체로 바인딩
    bindPrint(); //person1이 출력
    ```
    
    - 사용자 정의 객체
    
    클래스에서는 생성자 , 또는 생성자 함수를 만들때 사용되는 this는 자신의 인스턴스로 정의
    
    ```jsx
    function Person(name , age){
    this.name = name;
    this.age = age;}
    
    let person1= new Person('김씨',20);
    console.log(person1);
    //{name : '김씨', age:20;}
    ```
    
    - Arrow Function에서 this
    
    화살표 함수에서 this를 사용하면 자신을 포함하고 있는 외부 scope의 this를 계승받는다 
    
    ```jsx
    let person = {
    name:'박가현',
    printThis:()=>{
    console.log(this);} //이때 this는 printThis함수를 감싼 person의 this를 계승받기에
    // window객체
    }
    ```
    
    - Strict Mode에서 this
    
    Strict mode에서는 기본 값을 window로 하지않고 undefined로 설정