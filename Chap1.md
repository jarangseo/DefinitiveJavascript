#Chap1 자바스크립트 소개
- 자바스크립트는 `웹 프로그래밍 언어`이다
- 대다수의 웹사이트, 데스크탑, 게임콘솔, 테블릿, 스마트폰 등에 포함된 최신 브라우저도 `자바스크립트 인터프리터`를 내장하고 있다
- 반드시 배워야할 세가지 기술 중 하나
- `HTMl`로 웹 페이지의 내용 작성, `CSS`로 웹 페이지의 디자인 작성, `자바스크립트`로 웹 페이지의 동작 작성
- 객체 지향 프로그래밍과 함수형 프로그래밍 스타일을 잘 표현할 수 있는 고수준의, 동적이고, 타입을 명시할 필요가 없는 인터프리터 프로그래밍 언어
- 자바에서 문법을 가져왔고 Scheme에서 1급 함수의 개념을 가져옴, self에서 프로토타입 개방 상속 개념을 가져옴
- 썬마이크로시스템(지금의 오라클)에서 상표권 라이센스를 가지고, 언어구현은 넷스케이프(지금의 모질라)에서 담당
- 넷스케이프는 언어를 공식적으로 ECMA(European Computer Manufacturer's Association)에 제출했고, 제출한 언어의 이름을 ECMAScript로 정했다
- 마이크로소프트가 제작한 언어는 JScript
- 자바스크립트 언어 코어에는 텍스트나 배열, 날짜, 정규표현식을 다루기 위한 최소한의 API를 정의
- 입출력, 통신, 파일 저장, 그래픽 처리와 같이 복잡한 기능들은 '호스트환경'에서 담당
- 예를들어 클라이언트 측 자바스크립트는 브라우저가 언어 엔진을 내장하므로 호스트 환경은 브라우저가 됨
- 보통 자바스크립트 호스트 환경은 웹브라우저
- 모든 웹브라우저에는 자바스크립트 인터프리터가 내장되어 있음

##1.1 자바스크립트 코어
```javascript
// '//'뒤에 오는 내용은 주석으로 간주한다
// 주석은 해당 자바스크립트 코드를 설명하고 있다

// 변수는 값과 연관된 이름이다
// 변수는 var 키워드로 선언할 수 있다
var x; // 변수 이름을 x로 선언한다

// 값은 =기호를 통해 변수에 할당할 수 있다
x = 0; // 이제 x는 0의 값을 가진다
x // => 변수 x는 변수가 가진 값 0으로 평가된다

//자바스크립트는 다양한 타입의 값을 지원한다
x = 1; //숫자
x = 0.01; //정수나 실수
x = "hello world"; //큰따옴표로 둘러쌓인 문자열
x = 'JavaScript'; //작은따옴표로 둘러쌓인 문자열
x = true; //참을 뜻하는 불리언 값
x = false; //거짓을 뜻하는 불리언 값
x = null; // null은 값이 없음을 뜻하는 특별한 값
x = undefined; // undefined는 null과 유사

// 자바스크립트에서 가장 중요한 데이터 타입은 객체다
// 객체는 이름-값 쌍의 모음이다
// 값은 아무 자바스크립트 값이 될 수 있는 반면
// 이름은 반드시 자바스크립트 문자열이 와야한다
var book = { // 객체는 중괄호로 둘러쌓여 있다
	topic: "Javascript", // "topic"프로퍼티의 값은 "Javascript"다
	fat: true // "fat" 프로퍼티의 값은 true다
} // 닫는 중괄호는 객체 선언의 끝을 의미한다

//객체의 프로퍼티는 .과 []를 사요해 접근할 수 있다
book.topic // =>Javascript
book["fat"] // 객체의 프로퍼티에 접근하는 또다른 방법
book.author = "Flanagan"; // 객체에 값을 할당함으로써 새 프로퍼티를 생성한다
book.contents = {}; // {}는 고유 프로퍼티가 없는 빈 객체다

//자바스크립트는 숫자로 색인된 목록의 값을 담을 수 있는 배열도 지원한다
var primes = [2, 3, 5, 7]; // 배열에 네 값이 있고 []로 둘러 쌓여있다
primes[0] // =>2 : 배열의 첫번째 원소
primes.length // =>4 : 배열에 몇개의 원소가 있는지
primes[primes.length - 1] // => 7 : 배열의 마지막 원소의 값
primes[4] = 9 // 배열에 새 원소를 추가
primes[4] = 11 // 기존에 저장된 배열의 값을 변경
var empty = [], //원소가 없는 빈 배열
empth.length // => 0

//배열과 객체는 각각 원소와 프로퍼티의 값으로 배열과 객체를 가질 수 있다
var points = [ // 배열에 두 원소가 있다
	{x:0, y:0}, // 각 원소는 객체다
	{x:1, y:1}
];
var data = { // 객체에 두 프로퍼티가 있다
	trial1: [[1,2], [3,4]], // 각 프로퍼티의 값을 배열
	trial2: [[2,3], [4,5]] // 배열의 각 원소는 배열
}

//연산자 값(피연산자)들을 이용해 새 값을 산출한다
//가장 일반적인 산술 연산자는 다음과 같다
3 + 2 // 5
3 - 2 // 1
3 * 2 // 6
3 / 2 // 1
points[1].x - points[0].x // 1
"3" + "2" // 32 (연산자로 두 문자열을 이어붙인다)

//자바스크립트는 몇 가지 산술 연산자 단축 표현식을 정의하고 있다
var count = 0; //정의
count++; //증가
count--; //감소
count += 2; //2를 더한다
count *= 3; //3을 곱한다
count //변수 이름 또한 표현식이다

//등호와 관계연산자
//true나 false로 평가된다
var x = 2, y = 3; //=기호는 동등비교검사가 아닌 할당을 의미
x == y; // false 값이 같은지 비교
x != y // true 값이 다른지 비교
x < y //true 값이 작은지 비교
x <= y //true 값이 작거나 같은지 비교
x > y //false 값이 큰지 비교
x >= y //false 크거나 같은지 비교
"two" == "three" //false 두 문자열은 서로 다른다
"two" > "three" //true 알파벳순으로 봤을 때 tw는 th보다 크다
false == (x > y) //true false는 false와 값이 같다

//논리 연산자는 불리언 값들을 결합하거나 반전시킬 수 있다
( x == 2 ) && ( y == 3 ) //true 두 비교식이 참이다
( x > 3 ) || ( y < 3 ) //false 두 비교식이 모두 참이 아니다
!(x == y) // true !연산자는 불리언 값을 반전시킨다

```
- 구절이 모여 표현식이, 표현식이 모여 문장이 된다. 완전한 형태의 문장을 구문이라고 한다
- 세미콜론으로 끝나는 행은 구문
- 구문은 프로그램 상태를 바꾸지만, 표현식은 프로그램 상태를 바꾸지 않는다
- 함수는 이름과 매개변수를 갖는 자바스크립트 코드 블록

```javascript
//함수는 호출할 수 있는 자바스크립트 코드블록으로 매개변수를 가질 수 있다
function plus1(x) { //함수이름은 plus1이고 매개변수 x를 갖는다
	return x+1; //매개변수로 전달받은 값에 1을 더해서 반환
}
plus1(y) //y가 3이면 3+1을 반환
var square = function(x) { //함수는 값이 되고 변수 square에 할당됨
	return x*x; //반환할 함수 값을 계산
}; //할당문의 값은 세미콜론으로 끝나야한다

square(plus1(y)) //하나의 표현식에 함수호출을 두번 사용

//함수는 객체의 프로퍼티로 할당될 수 있다
//이때, 프로퍼티로 할당된 함수를 '메서드'라고 한다
//모든 자바스크립트 객체는 메서드를 갖는다
var a = []; //빈 배열을 만든다
a.push(1,2,3); //push메서드는 배열에 원소를 하나 이상 추가한다
a.reverse(); //reverse메서드는 배열이 가진 원소의 순서를 역순으로 바꾼다

//기존에 정의된 메서드 외에 임의로 메서드를 정의할 수도 있다
//"this"키워드는 메서드가 정의된 객체 자신을 가리킨다
//아래 points.dist메서드 몸체에서 사용한 this는 points배열을 가리킨다
points.dist = function() { //두 점의 거리를 계산하는 메서드를 정의
	var p1 = this[0]; //배열의 첫번째 원소를 가리킨다
	var p2 = this[1]; //배열의 두번째 원소를 가리킨다
	var a = p2.x - p1.x; //두 점의 x좌표 차이
	var b = p2.y - p1.y; //두 점의 y좌표 차이
	return Math.sqrt(a*a + b*b); //Math.sqrt함수를 이용해서 제곱근을 구한다
};
```
//프로그램 구조를 제어하는 구문들
//조건문과 루프 같은 구문
```javascript
function abs(x) { //절대값을 계산하는 함수
	if (x <= 0) { //괄호안의 표현식의 값이 참이면
		return x; //if절 안의 코드를 실행
	} //if절의 끝을 나타낸다
	else { //else절은 if절에서 사용한 표현식이 false일 경우
		return -x;
	} //각절에 포함한 구문이 하나일 경우에 중괄호 생략할 수 있다
} //return 문은 if/else문에 포함될 수 있다

function factorial(n) { //팩터리얼을 계산하는 함수를 정의
	var product = 1; //product값을 1부터 시작
	while(n > 1) { //괄호안의 표현식이 참이면 while문의 중괄호 안의 구문들을 반복 실행
		product *= n; //product = product * n의 단축표현
		n--; //n=n-1의 단축표현
	}
	return product; //product를 반환
}
factorial(4) //4*3*2*1 = 24

function factorial2(n) { //루프를 사용한 팩터리얼 함수를 정의
	var product = 1; //역시 product값은 1부터 시작
	for(i=2; i<=n; i++) //i값을 2부터 n까지 증가
		product *= i //매 루프마다 구문을 실행, 루프 몸체에 구문이 하나일 경우 중괄호를 생략할 수 있다
	return product; //팩터리얼을 반환
}
factorial2(5) //1*2*3*4*5 = 120
```
- 2차원 좌표계를 표현하는 예제
//Point클래스의 인스턴스 객체는 r()메서드를 갖는데, 이 메서드는 좌표의 원점 간의 거리를 계산한다
```javascript
//객체를 초기화하기 위해 생성자 함수를 정의한다
function Point(x,y) { //생성자 이름의 첫글자는 대문자로 시작한다
	this.x = x; //this키워드는 새로생성된 객체를 가리킨다
	this.y = y; //생성자로 전달된 인자는 객체의 프로퍼티로 저장한다
} //값을 반환하지 않아도 된다

//new 키워드로 객체를 생성할 때 앞에서 정의한 생성자 함수를 사용한다
var p = new Point(1,1); //2차원좌표 (1,1)

//생성자 함수 Point의 prototype객체에 함수를 정의함으로써
//Point객체에 메서드를 정의한다
Point.prototype.r = function() {
	return Math.sqrt( //x^2 + y^값의 제곱근을 반환한다
			this.x * this.x + //this는 이 메서드가 호출된 포인트 객체를 가리킨다
			this.y * this.y
		);
};

//Point객체 p(뿐만 아니라 모든 Point 객체)는 메서드 r()을 상속받는다.
p.r() // 1.414...
```
##1.2 클라이언트 측 자바스크립트
- 자세한 내용은 2부에서
- 클라이언트 측 자바스크립트 프로그래밍 기법의 기초를 심층 예제를 통해 빠르게 살펴보자
- 13장<웹브라우저와 자바스크립트>에서 배우게 될 가장 중요한 부분은 자바스크립트 코드를 `script`태그를 통해 HTML파일에 내장할 수 있다는 점

```javascript
<html>
<head>
<script src="library.js"></script><!--자바스크립트로 작성된 라이브러리를 포함시킨다-->
</head>
<body>
<p>p태그는 HTML에서 문단을 뜻한다</p>
<script>
//이 부분은 HTML파일 안에 내장한 클라이언트 측 자바스크립트의 일부이다
</script>
<p>그 밖에 다른 HTML태그가 올 수 있다.</p>
</body>
</html>
```

-14장<Window객체>에서는 웹브라우저에서 자바스크립트를 작성하는 방법과 클라이언트측 자바스크립트에서 사용하는 몇 가지 중요한 전역함수들

```javascript
<script>
function moveon() {
	//모달 상자를 출력해서 사용자에게 질문을 한다
	var answer = confirm("Ready to move on?");
	//확인 버튼을 누를 경우, 브라우저는 새 페이지를 출력한다
	if( answer ) window.location = "http://google.com";
}
//위 스크립트를 1분 후에 실행한다
setTimeout(moveon, 60000);
```

- 15장<문서 스크립팅>은 HTML문서를 스크립트를 사용해서 조작하는 방법을 다룬다
- HTML문서에 포함된 특정 엘리먼트를 찾거나, 찾은 HTML엘리먼트의 속성을 다루는 방법 혹은 엘리먼트에 표현된 콘텐츠 내용을 바꾸거나 새로운 엘리먼트를 추가하는 방법을 설명

```javascript
//문서의 디버깅 영역에 메세지를 출력한다
//만약 디버깅 영역이 존재하지 않으면 생성한다
function debug(msg) {
	//id속성을 사용해서 디버깅을 위한 영역을 찾는다
	var log = document.getElementById("debuglog");

	//만약 id가 "debuglog"인 엘리먼트가 없으면 임의로 생성한다
	if (!log) {
		log = document.createElement("div"); //새 <div>엘리먼트를 만든다
		log.id = "debuglog"; //엘리먼트의 id값을 "debuglog"로 한다

		log.innerHTML = "<h1>Debug Log</h1>"; //엘리먼트의 내용을 정의한다

		document.body.appendChild(log); //문서의 끝에 엘리먼트를 추가한다
	}

	//메시지를 <pre>엘리먼트의 텍스트 노드로 설정한 후,
	//디버깅 영역에 출력한다
	var pre = document.createElement("pre"); //pre엘리먼트를 만든다
	var text = document.createElement("text"); //text엘리먼트를 만든다

	pre.appendChild(text); //text노드를 pre에 추가
	log.appendChild(pre); //pre엘리먼트를 디버깅 영역에 추가
}
```

- 16장<CSS스크립팅>에서는 CSS스타일을 정의하는 방법을 설명
- HTML엘리먼트의 style또는 class 속성을 사용

```javascript
function hide(e, reflow) { //엘리먼트e의 스타일을 스크립트를 사용해 숨긴다
	if (reflow) { //두 번째 인자가 true면
		e.style.display = "none"; //엘리먼트가 차지한 공간을 숨긴다
	}
	else {//두 번째 인자가 true가 아니면,
		e.style.visibility = "hidden"; //엘리먼트가 차지한 공간을 그대로 두고, 내용을 숨긴다
	}
}
function highlight(e) { //엘리먼트 e에 CSS클래스를 설정해서 하이라이트효과를 설정
	//속성을 정의하거나 이미 정의되어있는 class속성에 새로운 값을 추가
	//기존에 hilite라는 클래스가 CSS스타일시트에 정의되어 있다고 가정한다
	if (!e.className) e.className = "hilite";
	else e.className += " hilite";
}
```

- 이벤트 핸들러는 브라우저에 등록하는 자바스크립트 함수로, 특정 이벤트가 발생했을 때 브라우저는 해당 이벤트에 등록된 이벤트 핸들러를 호출한다
- 17장<이벤트 핸들링>은 이벤트 핸들러를 정의하고 등록하는 방법과 특정 이벤트가 발생했을 때 브라우저가 해당 이벤트 핸들러를 어떻게 호출하는 지 설명
- 가장 손쉽게 이벤트 핸들러를 등록하는 방법은 HTML엘리먼트 속성에 "on"으로 시작하는 이벤트 핸들러를 지정하는 것
- 앞에서 다룬 debug()와 hide()함수를 debug.js, hide.js에 저장하고 아래의 예제를 만들었다

```javascript
<script src="debug.js"></script>
<script src="hide.js"></script>
Hello
<button onclick="hide(this, true); debug('hide button 1');">Hide1</button>
<button onclick="hide(this); debug('hide button 2);">Hide2</button>
world
```

- 다음 예제는 "load"이벤트에 이벤트 핸들러를 등록하는 것

```javascript
//"load"이벤트는 문서 로딩이 완료될 때 발생
window.onload = function() {
	//모든 <img>태그를 찾는다
	var images = document.getElementByTagName("img");
	//모든 <img>태그에 '클릭'행위가 일어날때
	//해당 이미지를 숨기는 이벤트 핸들러를 등록
	for ( var i = 0 ; i < images.length; i++ ) {
		var image = images[i];
		if( image.addEventListener ) //핸들러를 등록하는 또 다른 방법
			image.addEvnetListener("click", hide, false);
		else //IE8이나 이전 버전용
			image.attachEvent("onclick", hide);
	}
	//<img>태그에 등록할 이벤트 핸들러 함수
	function hide(event) { event.target.style.visibility = "hidden"; }
};
```

- API중 어떤 것은 사용하기 복잡하고, 일부 API는 특정브라우저에서 제대로 작동하지 않을 수 있다
- 이러한 이유로, 기본적인 프로그래밍 작업을 단순화 하기 위해 특정 라이브러리나 프레임워크를 선택
- 가장 유명한 라이브러리는 jQuery
- jQuery는 주요 브라우저에 대해 철저히 테스트되고 있어서 IE6에서도 잘 동작
- jQuery는 $()형태의 함수 이름을 빈번하게 사용
- debug()함수를 jQuery를 사용해 다시 작성하기

```javascript
functio debug(msg) {
	var log = $("#debuglog"); //메시지가 출력될 엘리먼트를 찾는다
	if (log.length == 0) { //해당 엘리먼트가 존재하지 않으면 생성한다
		log = $("<div id='debuglog'><h1>Debug Log</h1></div>");
		log.appendTo(document.body); //생성한 엘리먼트를 문서 젤 하단에 추가한다
	}
	log.append($("<pre/>").text(msg)); //<pre>안에 메시지를 생성하여 출력될 영역에 추가한다
}
```

