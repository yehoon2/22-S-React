## 자바스크립트 (JavaScript)

### 연산자

- 산술 연산자

    숫자 뿐 아니라 문자열도 산술 연산자 사용 가능
    
    ```js
    console.log(20 + 10); //30
    console.log(20 - 10); //10
    console.log(20 * 10); //200
    console.log(20 / 10); //2
    console.log(20 % 10); //0
    console.log("20" + "10"); //2010
    console.log("20" – "10"); //10
    console.log("20" * "10"); //200
    console.log("20" / "10"); //2
    console.log("20" % "10"); //0
    ```
    
- 증감 연산자
    
    ```js
    var num = 10;
    console.log(++num); //num+1 후 num 출력
    console.log(--num); //num-1 후 num 출력
    console.log(num++); //num 출력 후 num+1
    console.log(num--); //num 출력 후 num-1
    ```
    
- 비교 연산자

    ```js
    console.log(10 == 20); //값이 같다
    console.log(10 === 20); //데이터 타입과 값이 같다
    console.log(10 !== 20); //값이 같지 않다
    console.log(10 > 20);
    console.log(10 >= 20);
    console.log(10 < 20);
    console.log(10 <= 20);
    ```

- ==와 ===의 차이

    Boolean 데이터 타입인 true 혹은 false 반환

    ```js
    console.log(10 == "10"); //true
    console.log(10 === "10"); //false
    ```

- 논리 연산자

    ```js
    //앞 뒤 조건 모두 참인 경우에만 true 반환하는 AND연산자
    console.log(10 === 10 && 20 === 30);

    // 둘 중 하나만 참이여도 true 반환하는 OR연산자
    console.log(10 === 10 || 20 === 30);
    ```

### 조건문

- if 문

    if ( 조건 ) { 수행할 명령 } 만약 a<b가 참이라면 중괄호 안의 코드를 실행
    조건이 true면 if문 false면 else문 실행

    ```js
    var a = 20;
    var b = 40;

    if ( a < b ) {
    console.log("a는 b보다 작다.");
    } else {
        console.log("a는 b보다 작거나 같다.");
    }
    ```

- else if 문

    여러 개의 조건문을 생성할 때 사용

    ```js
    var a = 20;
    var b = 40;
    var c = 60;
    if ( a > b ) { console.log("a는 b보다 크다.");
    } else if ( b > c ) { console.log("b는 c보다 크다.");
    } else if ( a < c ) { console.log("a는 c보다 작다.");
    } else if ( b < c ) { console.log("b는 c보다 작다.");
    } else { console.log(“모든 조건을 만족하지 않는다.”);
    }
    ```

- 중첩 if 문

    if문 안에 또다른 if문을 삽입할 때 사용

    ```js
    var a = 20;
    var b = 40;

    if ( a !== b ) {
        if (a > b) { console.log(“a는 b보다 크다”); } 
        else { console.log("a는 b보다 작다”); }
    } else { console.log("a와 b는 같다”); }
    ```

### 반복문

- 반복문이 필요한 경우

    ```js
    console.log( 2 * 1 );
    console.log( 2 * 2 );
    console.log( 2 * 3 );
    console.log( 2 * 4 );
    console.log( 2 * 5 );
    .
    .
    console.log( 2 * 9 );  // left : 고정값, right : 가변값
    ```

- for 문

    for ( 초기화한 변수값; 조건; 증감 표시) { 수행할 명령 }

    ```js
    for (var i = 0; i < 10; i++) {
        console.log(i);
    }
    ```

- while 문

    while ( 조건 ) { 수행할 명령 } num<10 이 참일 동안 중괄호 안의 코드를 실행

    ```js
    var num = 0;

    while (num < 10) {
        console.log(num);
        num++;
    }
    ```

- do ~ while 문

    do { 수행할 명령 } while ( 조건 ) ; while의 조건과 관계 없이, do의 명령을 무조건 실행부터 한다.

    ```js
    var i = 12;

    do {
        console.log(i);
        i++;
    } while (i < 10);
    ```

