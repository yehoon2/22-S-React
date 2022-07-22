# 3주차

### Call-back

함수를 매개변수로 던지고, 특정 조건이 발생하면 해당 함수를 호출.

기본형 call-back구현은 간단한 비동기 함수 호출에는 유리하나, 복잡한 작업에서는

잘못하면 콜백 지옥 발생

### Promise

Promise에 등록한 Call back으로 던진 함수가 완료되면, then/catch/finally 구문을 수행

다중 콜백이 필요했던 case를 간소화할 수 있음

### async & await

새로운 API는 아니고, promise api를 wrapping(syntactic sugar) 처리한 기능

비동기 처리할 함수를 async로 선언하고, Promise API 앞에 await를 추가. 

(await은 Promise & Promise를 return하는 함수 앞에 붙어야함)

**Callback**

****

자바스크립트의 함수는 객체이다.

1. 변수나 데이터안에 담길 수 있다.

2. 매개변수로 전달 할 수 있다.

3. 반환 값으로 사용할 수 있다.

4. 실행도중에 생성될 수 있다.

콜백함수는 이 중에서 2번째 특징을 활용한 것으로

간단하게 다른 함수에 매개변수로 넘겨준 함수를 말한다.

매개변수로 넘겨받은 함수는 일단 넘겨받고, 때가 되면 나중에 호출(Called back)하는 것이 콜백함수이다.

function checkGang(count, link, good) {
  count < 3 ? link() : good();
}

checkGang 함수에 count 라는 정수 변수와, link와 good라는 함수가 변수로 들어가 있다.

이후 count값에 따라 link나 good 함수가 나중에 호출(Called back) 되는 것이다.

콜백함수가 사용되는 이유는 무엇일까?

변수의 유호범위(scope)와 동기/비동기(Synchronous/Asynchronous) 처리에 대해 알아야 한다.

자바스크립트는 스레드가 하나인 프로그램이기 때문에

프로그램의 속도를 높이기 위해 비동기 처리를 하게 된다.

하지만 프로그램 중에는 다른 함수의 return 값을 받고 그 값에 따른 함수를 사용해야하는 동기 방식의 함수도 필요하다.

그렇기에 called back 함수를 사용하여 순서대로(동기적으로) 함수를 사용할 수 있게 한다.

//﻿JavaScript is synchronus.
//Execute the code block in order after hoisting
//hoisting: var, function declaration

console.log('1');
setTimeout( () => console.log('2'), 1000);
console.log('3');
//1 3 2

//Synchronous callback
function printImmediately(print) {
 print();
}
printImmediately(() => console.log('Immediately'));

//Asynchronous callback
function printWithDelay(print, timeout) {
 setTimeout(print, timeout);
}
printWithDelay(() => console.log('async callback'), 2000);

//1 3 Immediately 2 async callback

//Callback Hell example
class UserStorage {
 loginUser(id, password, onSucces, onError) {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    onSucces(id);
   } else{
    onError(new Error('not found'));
   } 
  },2000);
 }

 getRoles(user, onSuccess, onError) {
  setTime(() => {
   if (user === 'ellie') {
    onSuccess({name: 'ellie', role: 'admin'});
   } else {
    onError(new Error('no acces'));
   } 
  }, 1000);
 }
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

user.loginUser(
 id, 
 password, 
 (user) => {
  getRoles(
   user, 
   (userWithRole) => alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`);
   (err) => console.log(err)
  );
}, (err) => console.log(err));

**하지만!!**

이 콜백 함수 또한 단점이 있었으니,

콜백은 함수의 매개변수로 함수를 넣기 때문에 가독성이 매우 떨어진다.

거기에 콜백에 콜백에 콜백이 무는 로직을 짜야하는 복잡한 경우가 생기게 되었다.

이로인해 가독성 뿐만 아니라 오류 찾기도 힘들어지자 이를 보안하고 나온 것이 바로.

Promise 함수이다.

---

**Promise**

****

콜백함수와 달리 실행과 동시에 함수를 전달하지 않고

then()을 이용해서 콜백 함수를 첨부하는 방식으로 바뀌었다.

const checkGang = new Promise((resolve, reject) => {
  count < 3 ? resolve(line) : resolve(good);
}

checkGang
 .then((status) => {console.log(status)});

//Promise is a JS object for asynchronous operation.
// state: pending -> fulfilled or rejected
// Producer vs Consumer

//1. Producer
// when new Promise is created, the executor runs automatically!!!
const promise = new Promise( (resolve, reject) => {
 //this is executor
 //doing some heavy work (EX: network, read files...)
 console.log('doing something...');
 setTimeout( () => {
  //resolve('ellie');
  //reject(new Error('no network'));
 }, 2000);
}); 
//doing something...

// 2.Consumers: then, catch, finally
promise
 .then( value => {
  console.log(value); //ellie
 })
 .catch(error => {
  console.log(error); //no network
 })
 .finally( () => {
  console.log('finally'); //finally
 });
 
// 3.Promise chaining
const fetchNumber = new Promise((resolve, reject) => {
 setTimeout( () => resolve(1), 1000);
});

fetchNumber
 .then(num => num * 2) //2
 .then(num => num * 3) //6
 .then(num => {
  return new Promise((resolve, reject) => {
   setTimeout( () => resolve(num-1), 1000);
  });
 }) //5
 .then( num => console.log(num)); //5 (2 seconds)

// Error Handling
const getHen = () =>
 new Promise((resolve, reject) => {
  setTimeout(() => resolve('Hen'), 1000);
 });

const getEgg = hen =>
 new Promise((resolve, reject) => {
  //setTimeout(() => resolve(`${hen} => Egg`), 1000);
  //setTimeout(() => reject(new Error('no egg'), 1000);
 });

const cook = egg =>
 new Promise((resolve, reject) => {
  setTimeout(() => resolve(`${egg} => Cook`), 1000);
 });

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)); //.then(console.log);
//Hen => Egg => Cook

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)) //.then(console.log);
 .cath( error => console.log(error)); //.then(console.log);
//no egg

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .catch( error => return 'Man')
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)); //.then(console.log);
//Man => Cook

//Callback Hell example
class UserStorage {
 
 loginUser = (id, password) => return new Promise((resolve, reject) => {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    resolve(id);
   } else{
    reject(new Error('not found'));
   } 
  },2000);  
 });

 getRoles = user => return new Promise((resolve, reject) => {
  setTime(() => {
   if (user === 'ellie') {
    resolve({name: 'ellie', role: 'admin'});
   } else {
    reject(new Error('no acces'));
   } 
  }, 1000);
 });
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

user.loginUser(id, password)
 .then((user) => user.getRoles(user)) //.then(user.getRoles)
 .then( (userWithRole) => alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`))
 .catch(console.log);

---

**async, await**

//clear style of using promise

//1. async

//function
function fetchUser() {
 //do network request in 10 secs...
 return 'ellie';
}

const user = fetchUser();
console.log(user); //10secs later.. and ellie

//promise
function fetchUser() {
 return new Promise((resolve, reject) => {
  //do network request in 10 secs...
  resolve('ellie');
 });
}

const user = fetchUser();
console.log(user); //ellie

//async 
//async function == promise
async function fetchUser() {
 //do network request in 10 secs...
 return 'ellie';
}

const user = fetchUser();
console.log(user); //ellie

//2. await

//promise
function delay(ms) {
 return new Promise(resolve => setTimeout(resovle, ms));
}

function getApple() {
 return delay(3000)
 .then(() => "Apple")
}

function getBanana() {
 return delay(3000)
 .then(() => "Banana");
}

function pickFruits() {
 return getApple()
 .then((apple) => {
  return getBanana().then(banana => `${apple} + ${banana}`);
 });
}
 
pickFruits().then(console.lob); //Apple + Banana

//await
function delay(ms) {
 return new Promise(resolve => setTimeout(resovle, ms));
}

async function getApple() {
 await delay(3000);
 return "Apple";
}

async function getBanana() {
 await delay(3000);
 return "Banana";
}

async function pickFruits() {
 try{
  const apple = await getApple(); //3secs await 
  cosnt banana = await getBanana(); //apple 3초 기다린 후 다시 3초
  return `${apple} + ${banana}`; //6secs await....
 } catch(err){
  console.log(err);
 }
}
 
pickFruits(); //Apple + Banana

//병렬처리
async function pickFruits() {
 try{
  const applePromise = getApple(); //실행
  const bananaPromise = getBanana(); //실행
  const apple = await applePromise; //3secs await
  cosnt banana = await bananaPromise; //3secs await
  return `${apple} + ${banana}`; //3secs await....
 } catch(err){
  console.log(err);
 }
}

//3. useful Promise APIs (병렬처리 코드 더러워)
function pickAllFruits() {
 return Promise.all([getApple(), getBanana()]).then(fruits =>
  fruits.join('+')
 );
}
pickAllFruits().then(console.log); //Apple + Banana

function pickOnlyOne() {
 return Promise.race([getApple(), getBanana())]);
}
pickOnlyOne().then(console.log);//Apple

//Callback Hell example
class UserStorage {
 
 loginUser = (id, password) => return new Promise((resolve, reject) => {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    resolve(id);
   } else{
    reject(new Error('not found'));
   } 
  },2000);  
 });

getRoles = user => return new Promise((resolve, reject) => {
  setTime(() => {
   if (user === 'ellie') {
    resolve({name: 'ellie', role: 'admin'});
   } else {
    reject(new Error('no acces'));
   } 
  }, 1000);
 });
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

try{
 const users = await user.loginUser(id, password);
 const userWithRole = await user.getRoles(users);
 alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`);
} catch(err){
 console.log(err)
}

**[출처]** [10. Call back, Promise, async/await](https://blog.naver.com/leeminwok/222578775551)|**작성자** [IMNOOK](https://blog.naver.com/leeminwok)

# Blocking(블로킹) / Non-blocking(논블로킹)

블로킹과 논블로킹은 A 함수가 B 함수를 호출했을 때, **제어권을 어떻게 처리하느냐에 따라 달라진다.**

### 1) 블로킹

**블로킹**은 A 함수가 B 함수를 호출하면, **제어권을 A가 호출한 B 함수에 넘겨준다.**

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2F8cdc0a02-d469-47d5-96c8-f6aeef204eb7%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2F8cdc0a02-d469-47d5-96c8-f6aeef204eb7%2Fimage.png)

1. A함수가 B함수를 호출하면 B에게 제어권을 넘긴다.
2. 제어권을 넘겨받은 B는 열심히 함수를 실행한다. A는 B에게 제어권을 넘겨주었기 때문에 함수 실행을 잠시 멈춘다.
3. B함수는 실행이 끝나면 자신을 호출한 A에게 제어권을 돌려준다.

### 2) 논블로킹

**논블로킹**은 A함수가 B함수를 호출해도 **제어권은 그대로 자신이 가지고 있는다**.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fc839fc04-1788-4063-ab38-b0d4a312dbf4%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fc839fc04-1788-4063-ab38-b0d4a312dbf4%2Fimage.png)

1. A함수가 B함수를 호출하면, B 함수는 실행되지만, **제어권은 A 함수가 그대로 가지고 있는다.**
2. A함수는 계속 제어권을 가지고 있기 때문에 B함수를 호출한 이후에도 자신의 코드를 계속 실행한다.

## 3. Synchronous(동기)와 Asynchronous(비동기)

동기와 비동기의 차이는 **호출되는 함수의 작업 완료 여부를 신경쓰는지의 여부**의 차이이다.

### 1) 동기

함수 A가 함수 B를 호출한 뒤, **함수 B의 리턴값을 계속 확인하면서 신경쓰는 것**이 동기이다.

### 2) 비동기

함수 A가 함수 B를 호출할 때 **콜백 함수를 함께 전달**해서, 함수 B의 작업이 완료되면 함께 보낸 콜백 함수를 실행한다.

함수 A는 함수 B를 호출한 후로 **함수 B의 작업 완료 여부에는 신경쓰지 않는다.**

## 4. 블로킹과 논블로킹, 동기와 비동기 비교

### 1) Sync-Blocking

동기를 블로킹처럼 실행하는 것은 이해하기 쉽다.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ff6212fee-ee42-4023-ae02-d2dc15eec46a%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ff6212fee-ee42-4023-ae02-d2dc15eec46a%2Fimage.png)

함수 A는 함수 B의 리턴값을 필요로 한다(**동기**). 그래서 제어권을 함수 B에게 넘겨주고, 함수 B가 실행을 완료하여 리턴값과 제어권을 돌려줄때까지 기다린다(**블로킹**).

### 2) Sync-Nonblocking

그런데, 동기를 논블로킹처럼 작동시킬 수 있다. 다음의 그림을 보자.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ffe5d1231-4c3c-4caf-bdd8-2287926e38ca%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ffe5d1231-4c3c-4caf-bdd8-2287926e38ca%2Fimage.png)

A 함수는 B 함수를 호출한다. 이 때 **A 함수는 B 함수에게 제어권을 주지 않고**, 자신의 코드를 계속 실행한다(**논블로킹**).

그런데 **A 함수는 B 함수의 리턴값이 필요하기 때문**에, 중간중간 B 함수에게 함수 실행을 완료했는지 물어본다(**동기**).

즉, 논블로킹인 동시에 동기인 것이다.

### 3) Async-Nonblocking

비동기 논블로킹은 이해하기 쉽다. A 함수는 B 함수를 호출한다.

이 때 제어권을 B 함수에 주지 않고, 자신이 계속 가지고 있는다(**논블로킹**). 따라서 B 함수를 호출한 이후에도 멈추지 않고 자신의 코드를 계속 실행한다.

그리고 B 함수를 호출할 때 **콜백함수**를 함께 준다. B 함수는 자신의 작업이 끝나면 A 함수가 준 콜백 함수를 실행한다(**비동기**).

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fb9566928-9a6b-4111-9cad-528daa45475d%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fb9566928-9a6b-4111-9cad-528daa45475d%2Fimage.png)

### 4) Async-blocking

Async-blocking의 경우는 사실 잘 마주하기 쉽지 않다.

A 함수는 B 함수의 리턴값에 신경쓰지 않고, 콜백함수를 보낸다(**비동기**).

그런데, B 함수의 작업에 관심없음에도 불구하고, A 함수는 B 함수에게 제어권을 넘긴다(**블로킹**).

따라서, A 함수는 자신과 관련 없는 B 함수의 작업이 끝날 때까지 기다려야 한다.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2F9b6754f0-8721-4308-8a62-d884c7315d15%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2F9b6754f0-8721-4308-8a62-d884c7315d15%2Fimage.png)

Async-blocking의 경우 sync-blocking과 성능의 차이가 비슷하기 때문에 사용하는 경우는 거의 없다.

# React 기본 개념 정리

**React의 탄생 배경**

데이터가 계속해서 변화하는 대규모 애플리케이션을 구축하기 위해 만들어진 라이브러리이다.

기존 뷰를 변경하는게 아닌, 기존 뷰를 날려버리고 새로 만들어버리면 어떨까?

**Virtual DOM**

real(기존) DOM을 일일히 변경하는 것이 아닌, virtual DOM을 만들어서 virtual DOM과 Real DOM을 비교하여 변화가 있는 부분만 업데이트한다. 리액트뿐만 아니라 Vue, Marko, Maquette, Mithril,..등에서 Virtual DOM 개념을 사용하고 있다.

![https://postfiles.pstatic.net/MjAyMDA4MTdfMjUg/MDAxNTk3NjQ3NDgyMzg2.9DUS2FzshDSXtZwYeCDivL6gUFSru243_yJ5CKPVUoAg.P9BT18o5YePnKLXG-OMOvgH7n1F-mIoOrbYXm4V1Zfwg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_3.57.15.png?type=w966](https://postfiles.pstatic.net/MjAyMDA4MTdfMjUg/MDAxNTk3NjQ3NDgyMzg2.9DUS2FzshDSXtZwYeCDivL6gUFSru243_yJ5CKPVUoAg.P9BT18o5YePnKLXG-OMOvgH7n1F-mIoOrbYXm4V1Zfwg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_3.57.15.png?type=w966)

**React의 특별한 이유**

- 어마어마한 생태계
- 사용하는 곳이 많다 (Airbnb, BBC, Cloudflare, facebook,..)
- 한번 사용하면 좋아하게 된다?..

**Webpack**

webpack은 코드들을 의존하는 순서대로 잘 합쳐서 하나 또는 여러개의 파일로 결과물을 만들어낸다. scss -> css로 변환해주는 등의 기능도 제공해주는 빌드 툴이다.

- webpack-dev-server : 별도의 서버를 구축하지 않고도 static 파일을 다루는 웹서버를 열 수 있으면, hot-loader를 통하여 코드가 수정 될 때마다 자동으로 리로드 되게 할 수 있습니다.

![https://postfiles.pstatic.net/MjAyMDA4MTdfMjY4/MDAxNTk3NjQ3OTAyODE4.8LygHVgrlAYXAYt9yEVywnVNrCRCmqSI2NV15hFpuxgg.BiB-2wPdou785eMi8gyH1s9Y8iqZugQ8_hIYsYLjglAg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.04.47.png?type=w966](https://postfiles.pstatic.net/MjAyMDA4MTdfMjY4/MDAxNTk3NjQ3OTAyODE4.8LygHVgrlAYXAYt9yEVywnVNrCRCmqSI2NV15hFpuxgg.BiB-2wPdou785eMi8gyH1s9Y8iqZugQ8_hIYsYLjglAg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.04.47.png?type=w966)

**Bable**
Babel is a JavaScript compiler

모든 브라우저에서 새로운 자바스크립트 문법을 지원하지 않으므로, 이전 버전의 자바스크립트 문법으로 변환해주는 컴파일러이다.

![https://postfiles.pstatic.net/MjAyMDA4MTdfNjMg/MDAxNTk3NjQ4MjA4MTAy.siPHg4vLOAELKayYneqFM1gm8SX7rv0m1Cok6-aX6bAg.FarcEaXky9YPd73HuAVvC7AwJnkjQzIFIDwp3_vywlcg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.09.56.png?type=w966](https://postfiles.pstatic.net/MjAyMDA4MTdfNjMg/MDAxNTk3NjQ4MjA4MTAy.siPHg4vLOAELKayYneqFM1gm8SX7rv0m1Cok6-aX6bAg.FarcEaXky9YPd73HuAVvC7AwJnkjQzIFIDwp3_vywlcg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.09.56.png?type=w966)

**JSX**
Babel is a JavaScript compiler

- 리액트에서 사용되는 HTML과 비슷한 문법으로, 최종적으로는.
    
    babel에 의해 자바스크립트로 변환된다
    
- HTML이랑 비슷하지만, 지켜야할 규칙이 몇가지 있다.
- 꼭 닫혀야 하는 태그
- 두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸있어야한다.
- JSX 내부에서 자바스크립트 값을 사용하는 방법은 중괄호로 감싸는 것이다.
- JSX 내부에서 조건부 렌더링을 할 때는 보통 삼항 연산자를 사용하거나, AND 연산자를 사용합니다.
- IIFE(ImmedIately Invoked Function Expressions)

![https://postfiles.pstatic.net/MjAyMDA4MTdfMTk3/MDAxNTk3NjQ4OTYzOTY5.VmojNgwmHN2upRs6UG1MZSZ7ZJajidI6PTGUaRodLKYg.N4LkrnMXEqrmoc-Mbdmaz13oSaml9lSEby6JQRmU8ysg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.22.35.png?type=w966](https://postfiles.pstatic.net/MjAyMDA4MTdfMTk3/MDAxNTk3NjQ4OTYzOTY5.VmojNgwmHN2upRs6UG1MZSZ7ZJajidI6PTGUaRodLKYg.N4LkrnMXEqrmoc-Mbdmaz13oSaml9lSEby6JQRmU8ysg.PNG.npng92/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2020-08-17_%EC%98%A4%ED%9B%84_4.22.35.png?type=w966)

- style 이름들을 camelCase로 표현
- class -> className에 지정
- 주석은 //, 여러줄은 {/*멀티라인*/}

**Props와 State**

리액트에서 데이터를 다룰 때 사용되는 개념

props : 부모 컴포넌트가 자식 컴포넌트에게 값을 전달할 때 사용

//함수형 컴포넌트
import React, {Component} from 'react';

const MyName = ({name}) => {
    return (
        <div>
           안녕하세요! 제 이름은 {name} 입니다.
        </div>
    )
};

MyName.defaultProps = {
    name : 'velopert'
};

export default MayName;

**Node.js**

Node.js는 자바스크립트를 서버환경에서 실행하는 자바스크립트 런타임 입니다.

웹브라우저에서 JavaScript가 해석되면, Web API를 통해서 웹브라우저에서 결과가 나타납니다.

Node.js에서 JavaScript가 해석되면, libuv를 통해서 OS에서 결과가 나타납니다.

자바스크립트 런타임? 런타임이란 특정 언어로 만든 프로그램을 실행할 수 있는 환경을 뜻합니다. 따라서 노드는 자바스크립트 프로그램을 컴퓨터에서 실행할 수 있게 해줍니다. 기존에는 자바스크립트 프로그램을 인터넷 브라우저 위에서만 실행할 수 있었습니다.

Node.js를 통해서 webpack과 Babel을 사용하면 (빌드 과정) React 코드가 compatible version of JavaScript로 바뀌고, 다시 bundle 되어 브라우저에 올리기만 하면 되는 결과물이 나타납니다.

React의 의존성 관리는 npm을 사용하는게 가장 일반적 입니다. npm(자바스크립트 패키지 매니저)을 쓰려면 역시 Node.js가 필요합니다.

npm은 Node.js에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할과 패키지 설치 및 관리를 위한 CLI(Command line interface)를 제공합니다. 자신이 작성한 패키지를 공개할 수도 있고 필요한 패키지를 검색하여 재사용할 수도 있습니다.

ex) storybook, create-react-app,..

![https://postfiles.pstatic.net/MjAyMDA4MTdfMTYg/MDAxNTk3NjUyNzczODA0.jevPvBfARmxv-bPRXuhHOAr57C1Uuc3vhTIHP88TDkQg.x7eFL4XVSrSyBneEYkoy1fVdc2kfuAbstpOpon1Y8LIg.JPEG.npng92/023.jpg?type=w966](https://postfiles.pstatic.net/MjAyMDA4MTdfMTYg/MDAxNTk3NjUyNzczODA0.jevPvBfARmxv-bPRXuhHOAr57C1Uuc3vhTIHP88TDkQg.x7eFL4XVSrSyBneEYkoy1fVdc2kfuAbstpOpon1Y8LIg.JPEG.npng92/023.jpg?type=w966)

노드의 내부 구조

**레퍼런스**

자바스크립트의 동작원리 : [https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/#%EC%B0%B8%EA%B3%A0](https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/#%EC%B0%B8%EA%B3%A0)

자바스크립트 런타임 관련 글 : [https://thebook.io/006982/ch01/01/02/](https://thebook.io/006982/ch01/01/02/)

Node.js와 React의 관계 : [https://velog.io/@eungook/React%EC%99%80-Node.js%EC%9D%98-%EA%B4%80%EA%B3%84%EB%8A%94-%EC%AB%8C-%EA%B1%B4%EB%84%88%EA%B1%B4%EB%84%88%EC%97%90%EC%9A%94](https://velog.io/@eungook/React%EC%99%80-Node.js%EC%9D%98-%EA%B4%80%EA%B3%84%EB%8A%94-%EC%AB%8C-%EA%B1%B4%EB%84%88%EA%B1%B4%EB%84%88%EC%97%90%EC%9A%94)

Node란 : [https://medium.com/day34/node-js-%EB%85%B8%EB%93%9C%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%96%B4%EB%96%A0%ED%95%9C-%EA%B8%B0%EB%8A%A5%EB%93%A4%EC%9D%B4-%EC%9E%88%EB%8A%94%EA%B0%80-1-98e49e1100ab](https://medium.com/day34/node-js-%EB%85%B8%EB%93%9C%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%96%B4%EB%96%A0%ED%95%9C-%EA%B8%B0%EB%8A%A5%EB%93%A4%EC%9D%B4-%EC%9E%88%EB%8A%94%EA%B0%80-1-98e49e1100ab)

**SPA (Single Page Application)**

단일 페이지로 구성된 웹 어플리케이션을 말한다. SPA는 화면 이동시에 필요한 데이터를 서버사이드에서 HRML으로 전달받지 않고(= 서버 사이드 렌더링), 필요한 데이터만 서버로부터 JSON으로 전달 받아 동적으로 렌더링한다.

![https://postfiles.pstatic.net/MjAyMDA4MjNfODMg/MDAxNTk4MTY3NDEzMTM5.xkfPf0ljPPyY30qc7u4kYjR2D-XVwo2isW3f3eb2pGog.yhECI364BOQ9lNnpeZHByTXubE8GCklrclwH_4fGVGAg.JPEG.npng92/best-single-page-applications.jpg?type=w966](https://postfiles.pstatic.net/MjAyMDA4MjNfODMg/MDAxNTk4MTY3NDEzMTM5.xkfPf0ljPPyY30qc7u4kYjR2D-XVwo2isW3f3eb2pGog.yhECI364BOQ9lNnpeZHByTXubE8GCklrclwH_4fGVGAg.JPEG.npng92/best-single-page-applications.jpg?type=w966)

**장점**

화면 전체를 렌더링하지 않고 필요한 데이터만 받아서 렌더링 하기 때문에 효율적이고 화면이동이 빠르다.

**단점**

처음 화면 로딩시 모든 화면이 미리 준비되어야해서 로딩 시간이 오래걸린다.

**Axios**

브라우저, Node.js에서 Promise API를 활용하는 HTTP 비동기 통신 라이브러리입니다.

**[출처]** [React 기본 개념 정리](https://blog.naver.com/npng92/222063603285)|**작성자** [npng92](https://blog.naver.com/npng92)

# ****SPA vs MPA와 SSR vs CSR 장단점 뜻정리****

# **SPA vs MPA**

**SPA(Single Page Application)는 한 개(Single)의 Page로 구성된 Application이다.MPA(Multiple Page Application)는 여러 개(Single)의 Page로 구성된 Application이다.MPA는 새로운 페이지를 요청할 때마다 정적 리소스가 다운로드된다. 매번 전체 페이지가 다시 렌더링 된다.반면 SPA는 웹 에플리케이션에 필요한 모든 정적 리소스를 최초 한 번에 다운로드한다.그 이후 새로운 페이지 요청이 있을 때, 페이지 갱신에 필요한 데이터만 전달 받아서 페이지를 갱신한다.그래서 SPA를 CSR(Client Side Rendering) 방식으로 렌더링한다고 말한다.그래서 MPA를 SSR(Server Side Rendering) 방식으로 렌더링한다고 말한다.**

# **MPA(Multiple Page Application)**

**여러 개(Single)의 Page로 구성된 Application이다.MPA는 SSR(Server Side Application) 방식으로 렌더링한다.새로운 페이지를 요청할 때마다 서버에서 렌더링된 정적 리소스(HTML, CSS, JavaScript)가 다운로드된다.페이지 이동하거나 새로고침하면 전체 페이지를 다시 렌더링한다.**

![https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/MPA.png?resize=601%2C324&ssl=1](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/MPA.png?resize=601%2C324&ssl=1)

### **👍 MPA 장점**

**SEO 관점에서 유리하다.
    ◦ MPA는 완성된 형태의 HTML 파일을 서버로부터 전달받는다.따라서 검색엔진이 페이지를 크롤링하기에 적합하다.**

**첫 로딩 매우 짧다.**

**◦ 서버에서 이미 렌더링해 가져오기 때문이다.
    ◦ 그러나 클라이언트가 JS 파일을 모두 다운로드하고 적용하기전 까지는 각각의 기능은 동작하지않는다.**

### **👎 MPA 단점**

**새로운 페이지를 이동하면 ‘깜빡’인다. (UX)
    ◦ 매 페이지 요청마다 리로딩(새로고침) 발생.새로운 페이지를 요청할 때마다 전체 페이지를 다시 렌더링하기 때문이다.페이지 이동시 불필요한 템플릿도 중복해서 로딩 (성능)서버 렌더링에 따른 부하모바일 앱 개발시 추가적인 백엔드 작업 필요 (생산성)개발이 복잡해질 수 있다.**

# **SPA(Single Page Application)**

**한 개(Single)의 Page로 구성된 Application이다.SPA는 CSR(Client Side Rendering) 방식으로 렌더링한다.단 한 번만 리소스(HTML, CSS, JavaScript)를 로딩한다.그 후에는 데이터를 받아올 때만 서버와 통신한다.즉, 첫 요청시 딱 한 페이지만 불러오고 페이지 이동 시 기존 페이지의 내부를 수정해서 보여주는 방식이다.이를 클라이언트 관점에서 말하자면 최초 페이지를 로딩한 시점부터는 페이지 리로딩 없이 필요한 부분만 서버로 부터 받아서 화면을 갱신하는 것이다.필요한 부분만 갱신하기 때문에 네이티브 앱에 가까운 자연스러운 페이지 이동과 사용자 경험(UX)을 제공할 수 있다.Angular, React, Vue 등 프론트엔드 기술들이 나오면서 크게 유행하고 있다.**

![https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/SPA.png?resize=600%2C324&ssl=1](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/SPA.png?resize=600%2C324&ssl=1)

**그런데 CSR 방식으로 만든 SPA 앱은 검색엔진최적화(SEO)가 어렵다.일반적인 SPA 앱을 검색로봇 입장에서 보면 모든 페이지의 소스가 아래와 같이 보이다.검색엔진이 색인을 할 만한 컨텐츠가 존재하지 않는 것이다.**

**<html><head>  <title>Single Page Application</title>  <link rel="stylesheet" href="app.css" type="text/css"></head><body>  <div id="app"></div>  <script src="app.js"></script></body></html>**

👍 **SPA 장점**

**자연스러운 사용자 경험 (UX)
    ◦ 전체 페이지를 업데이트 할 필요가 없기 때문에 빠르고 ‘깜빡’ 거림이 없다.필요한 리소스만 부분적으로 로딩 (성능)
    ◦ SPA의 Application은 서버에게 정적리소스를 한 번만 요청한다.그리고 받은 데이터는 전부 저장해놓는다. (캐시=Cache)서버의 템플릿 연산을 클라이언트로 분산 (성능)컴포넌트별 개발 용이 (생산성)모바일 앱 개발을 염두에 둔다면 동일한 API를 사용하도록 설계 가능 (생산성)**

### **👎 SPA 단점**

**JavaScript 파일을 번들링해서 한 번에 받기 때문에 초기 구동 속도가 느리다. (Webpack의 code splitting으로 해결 가능)검색엔진최적화(SEO)가 어려움 (SSR로 해결 가능)보안 이슈 (프론트엔드에 비즈니스 로직 최소화)
    ◦ SSR에서는 사용자에 대한 정보를 서버측에서 세션으로 관리를 하지만 CSR 방식에서는 클라이언트측의 쿠키말고는 사용자에 대한 정보를 저장할 공간이 마땅치 않다.**

### **⚠️ 주의점**

**SPA 방식이 모두 CSR인 것은 아니다.**

# **SSR vs CSR**

SSR과 CSR 두 가지 렌더링 방식에 대해 살펴보았는데 다시한번 정리하자면 이렇다.

차이점으로 초기렌더링속도, SEO, 보안이 있다.

# **SSR이 렌더링하는 방식**

웹에 시작부터 MPA가 있었다. 사실 MPA라는 용어도 SPA와 비교를 위해 등장한 인상이 강하다. 웹의 초기부터 SPA에 대한 구현체들이 나오기 전까지는 전통적인 웹사이트들은 모두 MPA 형태로 서비스해 왔다.

MPA는 페이지를 이동할 때마다 새로운 페이지를 요청한다. 모든 템플릿은 서버 연산을 통해서 렌더링하고 완성된 페이지 형태로 응답한다. 이 과정을 서버 사이드 렌더링(SSR)이라고 부른다.

서버 사이드 렌더링의 장점은 SEO이다. 전통적인 MPA의 경우 브라우저에서 JavaScript 코드가 동작하기 전에도 완성된 형태의 템플릿 (HTML에 데이터가 삽입된 상태)을 서버로 부터 전달받는다. 이 때문에 검색로봇이 페이지를 크롤링하기에 매우 적합하다.

![https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/SSR.png?resize=599%2C427&ssl=1](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/SSR.png?resize=599%2C427&ssl=1)

# **CSR이 렌더링하는 방식**

최초에 한번 서버에서 전체 페이지를 로딩하여 보여주고 이후에는 사용자의 요청이 올 때마다, 리소스를 서버에서 제공한 후 클라이언트가 해석하고 렌더링하는 방식이다. SEO가 어렵다는 큰 단점이 있다.

![https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/CSR.png?resize=597%2C421&ssl=1](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/03/CSR.png?resize=597%2C421&ssl=1)

# 

# **[React] jsx**

## jsx란?

jsx란 javascript 와 xml를 합친 용어이고 자바스크립트를 확장한 문법이다jsx코드는 js안에 xml 형태로 마크업코드를 넣을수 있다jsx는 react에서 엘리먼트를 생성할때 사용된다.

```
const name = 'Josh Perez';

const element = <h1>Hello, {name}</h1>;

// 출력값 > Hello, Josh Perez
```

## jsx의 사용규칙

jsx는 babel을 통해 js파일로 트랜스파일되기 떄문에 jsx코드 작성시 지켜야할 규칙이 있다

1. 태그를 꼭 닫아야한다.`<div></div>`처럼 닫는 태그를 꼭 적어줘야하고,input, br같은 단일태그는 아래와 같이 self-closing을 꼭 해줘야 한다.
    
    ```
    <br />
    ```
    
2. 두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸져 있어야 한다.단순히 감싸는 용도로만 div를 사용하는것이 구조상 너무 복잡해질때는 fragment를 이용해서 감싼다(fragment는 dom node를 추가하지 않고 자식들을 그룹화 할수있다)
3. jsx안에서 자바스크립트 변수나 문법을 사용할때는 {}안에 적어줘야 한다.
4. 태그의 attribute 중 class와 for 대신 className과 htmlFor를 사용해줘야한다. class는 javascript에서 키워드이기 때문.

## jsx를 사용하는 이유

### React에서 element를 생성하는 방법

- React.createElement

```
// 형태
// React.createElement(element, props, ...children)

React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```

React.createElement를 사용할때 단점

1. 엘리먼트를 만들때마다 호출해야 하기때문에 코드가 길어질수있음
2. 엘리먼트 구조를 한눈에 보기힘들기 때문에 가독성이 떨어진다.
- jsx

```
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```

jsx는 js코드 내부에서 마크업코드를 작성 가능하기때문에 엘리먼트구조를 직관적으로 파악 할 수 있다.그리고 다른 메서드를 호출하지 않고도 바로 엘리먼트를 생성 할 수 있다.

jsx로 코드를 작성하더라도 jsx는 babel을 통해 React.createElement의 형태로 트랜스파일 된다.

## jsx의 장단점

### 장점

- 코드의 가독성을 높일수 있고, xml문법과 유사하여 중첩된 구조를 더 잘나타낼수있다.
- 자바스크립트의 확장문법이기 때문에 자바스크립트의 모든 기능과 문법을 사용할수 있다.

### 단점

- jsx는 빌드환경에서 트랜스파일 설정을 해줘야 한다. 하지만 CRA를 통해 파일을 만들면 babel이나 webpack같은 build도구를 따로 설정해주지 않아도 build시 내가 제작한 앱의 최적화된 build파일이 생성된다.

# [React] Rendering Elements

엘리먼트는 React 앱의 가장 작은 단위로, 화면에 표시할 내용을 기술한다. (엘리먼트가 모여서 컴포넌트가 된다.)

const element = <h1>Hello, world</h1>

리액트 엘리먼트는 immutable 하다. 엘리먼트를 생성한 이후에는 자식이나 속성을 변경할 수 없다.

UI를 업데이트하는 유일한 방법은 새 엘리먼트를 생성하고 ReactDOM.render()에 넘겨주는 것이다.

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);

**Virtual DOM**

****

웹 브라우저는 DOM을 활용하여 객체에 자바스크립트와 CSS를 적용한다. 하지만 DOM은 동적 UI에 최적화되어 있지 않다. DOM에 변화가 일어나면 웹 브라우저는 CSS를 다시 연산하고, 레이아웃을 구성하고, 페이지를 리페인트한다. 이 과정에서 시간이 허비되고, 업데이트가 너무 잦으면 성능이 저하될 수 있다.

리액트는 Virtual DOM을 사용하여 실제 DOM 전체를 조작하는 대신 바뀐 부분만 최소한으로 조작한다.

리액트에서 웹 브라우저에 실제 DOM을 업데이트할 때는 다음 세 가지 절차를 밟는다.

1. 데이터를 업데이트하면 전체 UI를 Virtual DOM에 리렌더링한다.

2. 이전 Virtual DOM에 있던 내용과 현재 내용을 비교한다.

3. 바뀐 부분만 실제 DOM에 적용한다.