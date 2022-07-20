React
	Meta에서 개발한 오픈 소스 자바스크립트 라이브러리
모듈형 개발이기 때문에 생산성이 높음 (부품을 자유롭게 떼었다 붙였다 할 수 있는 형태)
상호작용이 많은 UI를 만들 때 생기는 어려움을 줄여줌(SPA)
Virtual DOM을 활용하여 리렌더링이 잦은 동적인 모던 웹에서 엄청나게 빠른 퍼포먼스를 내는게 가능
컴포넌트 기반
	웹 UI를 작은 컴포넌트 단위로 구성
컴포넌트는 다른 프로젝트에서도 재사용할 수 있고, 컴포넌트 캡슐화(정보 은닉)와 확장이 가능해 개발이 유연해지는 장점이 있다
프레임워크가 아니라 라이브러리인지라 다른 프레임워크에 간편하게 붙여서 사용하는 것도 가능
프레임워크
소프트웨어 어플리케이션이나 솔루션의 개발을 수월하게 하기 위해 소프트웨어의 구체적 기능들에 해당하는 부분의 설계와 구현을 재사용 가능하도록 협업화된 형태로 제공하는 소프트웨어 환경
	어플리케이션 개발을 위한 뼈대를 제공해주는 역할
라이브러리
	소프트웨어를 개발할 때 프로그램이 사용하는 비휘발성 자원의 집합
	미리 작성된 코드, 변수, 클래스가 포함될 수 있음
개발하는데 필요한 것들을 모아둔 도구들의 나열로 필요할 때 호출하는 방식
프레임 워크 vs. 라이브러리
	flow에 대한 제어 권한이 어디에 있느냐의 차이
프레임 워크 : 전체적인 흐름을 자체적으로 가지고 있고 프로그래머가 그 안에 필요한 코드를 작성
라이브러리 : 사용자가 흐름에 대한 제어를 하며 필요한 상황에 가져다 씀
	
컴포넌트
		class형과 함수형이 존재
		React를 구성하고 있는 조각 하나하나를 말함
react는 사용자에게 보여지는 UI 요소를 컴포넌트 단위로 구분하여 구현
	함수형 컴포넌트
function 으로 정의하고 return 문에 jsx 코드를 반환
	클래스형 컴포넌트
class로 정의하고 render( ) 함수에서 jsx 코드를 반환

state(상태)를 사용할 수 있으며 각종 Life cycle 및 Method를 이용하여 컴포넌트가 Mount 혹은 Unmount 될 때 추가 작업을 수행시키는 등 조작을 할 수 있음. 하지만 Hook이 등장한 이후부터는 위 기능들을 함수형 컴포넌트에서도 대부분 구현이 가능하게 되었습니다.
	
	State
		컴포넌트가 관리하는 속성값(데이터)
		한 컴포넌트에서만 사용하는 정보를 넣고 생성, 수정하는 데이터
		함수 내에 선언된 변수처럼 컴포넌트 안에서 관리됨

	Hook
함수 컴포넌트에서 State와 Life cycle을 연동(hook into)할 수 있게 해주는 함수
		class를 작성하지 않고도 state와 다른 React의 기능들을 사용할 수 있게 해줌
	
	Virtual DOM
React는 DOM을 직접적으로 조작하지 않고 데이터가 변화할 때 변경사항이 적용된 Virtual DOM을 만듦	
	실제 DOM 변화를 최소화 시켜주는 역할
뷰에 변화가 있다면, 그 변화가 실제 DOM에 적용되기 전에 Virtual DOM에 적용시키고 최종 결과만 실제 DOM에 전달
	따라서 20개의 변화가 있다면 Virtual DOM은 변화된 부분만 가려내어 실제 DOM에 전달하고 실제 DOM은 그 변화를 1회로 인식하여 단 한번의 렌더링 과정만 거치게 됨

JSX
	Java Script eXtension
	XML을 기반
	React에서 HTML을 표현할 때, JSX를 사용
	빌드 시 Babel에 의해 자바스크립트로 변환
	자바스크립트 코드를 HTML처럼 표현할 수 있기 때문에 용이한 개발이 가능

SPA
	Single Page Application
	한개의 페이지로 구성된 웹서비스
기존페이지에 컴포넌트화된 서브 페이지나 적절한 자원, 데이터 등 만을 넘겨주어 Client 상에 Rendering이 이루어지는(CSR) 방식으로 동작
새로운 메뉴를 누르거나 신규등록, 데이터 삭제 등의 기능을 할 때, 새롭게 페이지가 새로고침되지않고, 필요한 리소스만 받아와 동적으로 빠르게 적용
데이터를 받아올 때만 서버와 통신함
페이지 리로딩 없이 화면을 갱신함
장점
	자연스러운 페이지 이동
	필요한 리소스만 부분적으로 로딩
	컴포넌트별 개발이 용이
	로컬 데이터를 효과적으로 캐시에 임시 저장 가능
	서버의 사용없이도 개발을 시작할 수 있음
단점
	초기 구동 속도가 느림
처음 웹 어플리케이션에 필요한 모든 정적 리소스를 한번에 받아옴
	SEO 관점에서 불리
	JS를 모르면 구현이 불가능
FaceBook, Google 등이 사용함

CSR
최초에 한번 서버에서 전체 페이지를 로딩하여 보여주고 이후에는 사용자의 요청이 올 때마다, 리소스를 서버에서 제공한 후 클라이언트가 해석하고 렌더링하는 방식이다. SEO가 어렵다는 큰 단점이 있다.

MPA
	Multi Page application
서버에 요청이 있을때마다 신규페이지를 불러와 그리는 방식(항상 전체 페이지가 다시 렌더링 됨)
여러 개(multi)의 Page로 구성된 application 으로 PHP, JSP 등의 서버사이드 언어로 서버 사이드 렌더링 (SSR)이 이루어진다
html로 작성된 여러 페이지들을 배포하여 서비스하는 경우가 MPA에 해당
MPA는 새로운 페이지를 요청할 때마다 페이지 리소스가 다운로드 되고,
그에 맞춰 전체 페이지를 다시 렌더링
장점
		SEO (Search Engine Optimization, 검색 엔진 최적화) 관점에서 유리
			검색엔진이 페이지를 크롤링하기에 적합
		완성된 형태의 HTML 파일을 서버로부터 전달받음
		SPA에 비해 첫 페이지 로딩이 매우 짧음
	단점
		페이지를 이동할떄마다 리로딩 발생
		프론트엔드와 백엔드가 결합되어 있음
			개발과 관리가 복잡하고 어려워질 수 있음
		서버 렌더링에 따른 부하가 발생함
		페이지 이동시 불필요한 템플릿 중복 로딩이 발생
	Amazon, The New York Times 등이 사용함
	전통적인 웹사이트들은 MPA형태로 서비스해옴

SSR
MPA는 페이지를 이동할 때마다 새로운 페이지를 요청한다. 모든 템플릿은 서버 연산을 통해서 렌더링하고 완성된 페이지 형태로 응답
		이를 SSR(서버 사이드 렌더링)이라고 부름
서버 사이드 렌더링의 장점은 SEO이다. 전통적인 MPA의 경우 브라우저에서 JavaScript 코드가 동작하기 전에도 완성된 형태의 템플릿 (HTML에 데이터가 삽입된 상태)을 서버로 부터 전달받는다. 이 때문에 검색로봇이 페이지를 크롤링하기에 매우 적합하다.

Life cycle
React Component는 탄생부터 죽음까지 여러 지점에서 개발자가 작업이 가능하도록 메서드를 오버라이딩 할 수 있게 해줌
component의 생성, 변경, 소멸 과정
component를 렌더링할 때(update) 어떤 작업을 처리하거나, 업데이트 전 후로어떤 작업을 처리해야 할 수도 있는데 이때 Life cycle 메소드를 사용
Life cycle 메소드는 class형 컴포넌트에서만 사용 가능
	함수 컴포넌트에서는 Hook을 이용하여 비슷한 처리 가능

Life cycle Method
		Mount – Update – Unmount로 나눌 수 있다
		Mount
			DOM이 생성되고 웹 브라우저에 나타나는 것을 말함
			constructor  getDerivedStateFromProps  componentDidMount
			순서로 발생함
			constructor
클래스 생성자. 처음 한 번만 실행되며 state 선언, props를 초기화 할 때 사용
			getDerivedStateFromProps
				컴포넌트가 새로운 props를 받게 됐을 때 state를 변경
			componentDidMount
				컴포넌트가 웹브라우저에 나타난 후 호출
화면에 모두 그려진 후에 실행되어야 하는 이벤트 처리, 초기화, 비동기 작업 처리 등 가장 많이 활용
		Update
			


		
			




		Unmount
			mount의 반대 과정으로 컴포넌트를 DOM에서 제거
			componentWillUnmount
				컴포넌트가 웹브라우저에서 사라지기 전 호출

사용자 정의 태그를 만드는 것과 react는 유사하다 - 이를 component라고 한다
	가독성이 좋고
	재사용성
	유지보수가 좋다

컴포넌트
	예를 들어 웹페이지의 header부분 전체를 TOP이라는 사용자 정의 태그안에 넣어놓고
	본문에서 TOP라는 태그를 가져다 쓰는 것이 component를 사용한는 것과 유사한 행위

npm
	node.js로 만들어진 프로그램을 쉽게 설치해주는 일종의 앱스토어
	먼저 node.js라는 프로그램을 깔아야 한다

react 준비하기
1. npm으로 create-react-app 설치하기
	Node.js prompt 들어가기
npm install -g create-react-app 입력
	create-react-app-V로 설치 확인이 가능
	안되면 sudo npm install create-react-app으로 설치

2. 개발환경 디렉토리 설정하기
	예) 바탕화면 -> react-app 이라는 파일 만들기
	이곳이 react가 작동할 디렉토리가 된다
	계속해서 prompt에서 cd (만든파일)로 이동하고
	create-react-app .  (.은 현재 파일이라는 뜻) 으로 개발환경 구축을 완료한다

3. 샘플 웹app으로부터 js 코딩 시작하기
	vscode – 만들파일의 터미널에서 npm start 을 입력하면 샘플 웹app을 만들어준다
	이를 기반으로 수정해가면 된다

4. 디렉토리 구조 파악하기
	public 디렉토리
		index.html이 있는 곳
			
	      create react app 은 react로 만든 컴포넌트들이 #root안에 들어가도록 설정 해놓음
	





src 디렉토리
		대부분의 개발에 관한 파일들은 이곳에 들어가게 된다
		index.js는 진입파일이다
							로 html의 #root에 연결된다
		
					render에 있는 <App/>이 componet이고
		실제 component에 대한 구현은 import를 통해서
						(실제로는 ./App.js 이다)
		App.js에서 이루어진다







컴포넌트 만들기
	








	public 폴더 안에 새롭게 pure.html이라는 파일과 header태그안에 내용을 집어넣은 상태
	개발환경인 App.js에서 컴포넌트화 시키기
1.	함수를 만든다 ex) Subject
2.	원하는 내용을 return문 안에 넣는다
3.	index.js가 실제로 받는 것은 App.js에서 App으로 설정해놨음으로 App함수안에 Subject 컴포넌트를 넣는다
	









+




App.js에 있는 다음과 같은 코드는 js가 아닌 jsx이다
jsx로 코드를 작성하면 create react app이 js로 변환 해준다.

Props(속성)


	









	기존의 방식의 component는 속성이 없다 하지만 props(속성)을 추가하면 
	어떤 텍스트가 어떤 속성으로 있는지 알 수 있다.



















또한 Subject라는 Component는 항상 <h1> WEB
과 world wide web!을 출력하는 역할이였지만















다음과 같이 title과 sub의 내용을 바꾸면 재사용이 가능하다.

Props & State
	state는 porps의 값에 따라서 내부에 필요한 데이터
	props와 state는 분리되어 있다
	
	render라는 메서드보다 먼저 실행되면서 component를 초기화 하고 싶을 때
	constructor을 사용한다
	
	
