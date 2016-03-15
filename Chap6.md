#6장 객체
- 이름과 값으로 구성된 프로퍼티들의 정렬되지 않은 집합
- 프로퍼티 이름은 문자열
- 객체는 문자열과 값이 연결된 집합
- 자바스크립트 객체는 객체가 가진 고유 프로퍼티를 유지하는 것 외에'프로토타입'이라고 하는 다른 객체의 프로퍼티를 상속받는다
- 객체의 매서드들은 일반적으로 상속받은 프로퍼티고, 이를 '프로토타입 상속'이라고 한다
- 프로토타입 상속은 자바스크립트의 핵심기능이다
- 자바스크립트 객체는 프로퍼티를 동적으로 추가하고 제거할 수 있다
- 정적 객체나 정적 타입 언어에서의 '구조체'처럼 사용할 수도 있다
- var y = x;에서 변수 y는 x와 같은 객체를 참조, 객체자체를 복사하지 않는다
- 프로퍼티 이름은 빈 문자열을 포함한 어떤 문자열이든 될 수 있다
- 객체가 같은 이름의 프로퍼티르 ㄹ두개 가질 수 없다 
- 쓰기속성 : 프로퍼티 값의 수정 가능 여부를 결정
- 열거속성 : 프로퍼티의 이름을 for/in 루프에서 읽을 수있는지 여부 결정
- 설정속성 : 프로퍼티 삭제 가능 여부와 프로퍼티 속성의 변경 여부 결정
- 객체의 prototype은 상속받은 프로퍼티들을 가진 객체에 대한 참조변수다
- 객체의 class 는 객체의 유형을 분류하는 문자열이다
- 객체의 extensible플래그는 새 프로퍼티의 추가 여부를 결정한다
- 네이티브 객체 : Array ,Function, Date, 정규표현식
- 호스트객체 : 인터프리터가 내장된 호스트 환경에 정의된 객체. HTMLElement객체는 웹페이지의 구조가 클라이언트 측 자바스크립트로 표현된 호스트 객체
- 사용자 정의 객체 : 자바스크립트 코드의 실행으로 생성된 객체
- 고유 프로퍼티 : 객체에 직접 코드로 정의한 프로퍼티
- 상속받은 프로퍼티 : 객체 프로토타입 객체에 의해 정의된 프로퍼티

##6.1 객체 생성하기
- 객체 리터럴 또는 new키워드를 이용해 생성
- Object, create()함수를 통해 생성

##6.1.1객체 리터럴
- 중괄호 안에 이름과 값을 쌍점으로 구분한 형태를 쉼표로 구분해 연결한 리스트
- 프로퍼티 이름으로 자바스크립트 식별자또는 문자열 사용, 프로퍼티 값으로 자바스크립트 표현식 사용
```javascript
	var empty = {};
	var point = {x:0, y:0};
	var point2 = {x:point.x, y:point.y+1};
	var book = {
		"main title": "Javascript",
		'sub-title': "The Definitive Guide",
		"for": "all audiences",
		author: {
			firstname: "David",
			surname: "Flanagan"
		}
	}
```

- ECMAScript5와 ECMAScript3 일부 구현에서 예약어를 인용부호로 감싸지 않고 프로퍼티 이름으로 사용할 수 있다
- ECMAScript5에서 객체 리터럴 마지막 프로퍼티 값 뒤에오는 쉼표는 무시, ECMAscript3는 대체로 무시하지만 IE에서는 Error로 간주한다
- 객체리터럴은 리터럴이 평가되는 시점에 새로운 객체가 생성됨과 동시에 초기화되는 표현식
- 각 프로퍼티의 값 또한 리터럴이 평가될때마다 새롭게 해석된다 즉 하나의 객체 리터럴은 수많은 객체를 만들 수 있다
- ex)객체리터럴이 함수 내부의 루프 몸체에 있는 경우

##6.1.2 new를 이용해 객체 생성하기
- new 연산자로 객체를 만들고 초기화할 수 있다
- new키워드는 반드시 함수 호출 다음에 와야한다
- 이때 사용되는 함수를 생성자라고 한다
- 새로 생성된 객체를 초기화 하는 역할을 한다
- 코어자바스크립트는 원시타입을 위해 내장(built-in)생성자를 포함하고있다
```javascript
	var o = new Object();
	var a = new Array();
	var d = new Date();
	var r = new RegExp("js");
```

##6.1.3프로토타입
- 자바스크립트 모든 객체는 두번째 자바스크립트 객체와 연관되어있다
- 두번째 객체는 프로토타입으로 알려져있고, 첫번재 객체는 프로토타입으로부터 프로퍼티들을 상속받는다
- 객체 리터럴로 생성된 모든 객체는 프로토타입 객체가 같으며, 이 프로토타입객체는 Object.prototype으로 참조할 수 있다
- new키워드를 사용해 생성자를 호출하면, 생성자의 프로토타입을 자신의 프로토타입으로 하는 객체가 생성된다
- new Object()로 생성된 객체는 Object.prototype을 상속받으며, {}로 생성된 객체와 동일하다. 
- new Array()로 생성된 객체는 Array.prototype을 객체의 프로토타입으로 사용
- new Date()로 생성된 객체는 Date.prototype을 객체의 프로토타입으로 사용
- Object.prototype은 prototype이 없다, 즉 아무런 프로퍼티도 상속받지 않는다
- 모든 내장된 생성자, 사용자 정의 생성자는 프로토타입을 갖는데 Object.prototype을 상속받는다
- Date.prototype은 Object.prototype의 프로퍼티들을 상속받는다
- Date객체는 new Date()를 통해 만들어지며 Object.prototype과 Date.prototype을 전부 상속한다
- 프로토타입 객체들의 연속된 연결을 '프로토타입 체인'이라 한다

##6.1.4 Object.creat()
- Object.creat()는 새 객체의 정보를 가진 객체를 두번째 인자로 갖는데 이 인자는 생략할 수 있다
```javascript
	var o1 = Object.creat({x:1, y:2}); //o1은 x,y프로퍼티를 상속받는다
```
- 프로토타입을 갖지 않는 새 객체를 만들기 위해서는 함수에 null을 전달하면 된다
- 이런경우, 새로 생성된 개게가 어떤 객체도 상속받지 않으므로 toString()메서드와 같은 기본 메서드도 사용할 수 없다
```javascript
	var o2 = Object.creat(null); //o2은 프로퍼티와 메서드가 없다
```
- {}, new Object()로 생성된 객체처럼 일반적인 빈 객체 만들고 싶으면 Object.prototype을 전달한다
```javascript
	var o3 = Object.creat(Object.prototype); //o3은 {}, new Object()와 같은 객체다
```

```javascript
//inherit()는 프로토타입 객체 p의 속성을 상속받아 새롭게 생성된 객체를 반환한다
	function inherit(p) {
		if ( p == null ) throw TypeError(); //p는 null이 아닌 객체여야한다
		if ( Object.create ) //Object.create을 사용할 수 있으면
			return Object.create(p); //이를 사용한다
		var t = typeof p; //객체의 타입검사가 더 필요한 경우 아래와 같이 한다

		if(t !== "object" && t !== "function") throw TypeError();
		function f() {}; //임시로 빈 생성자 함수 정의
		f.prototype = p; //프로토타입 p의 프로퍼티를 설정
		return new f(); //p를 상속하는 객체를 만들기 위해서는 함수  f()를 사용한다
	}
```
- inherit()메서드는 인자로 받은 객체의 프로퍼티를 상속받은 새 객체를 반환한다
- 객체 생성시 빈 프로토타입 객체를 통해 만들 수 없다
- Object.create()의 두번째 인자와 같은 선택인자를받지않는다

##6.2 프로퍼티 접근 및 설정
- 프로퍼티의 값 가져오기 위해 마침표연산자 또는 대괄호 연산자를 사용
- 연산자 좌측에는 객체로 평가되는 표현식이온다
- 연산자 우측에는 프로퍼티이름이 식별자로 와야한다
- 대괄호 안에는 프로퍼티 이름의 문자열로 평가되는 표현식이 와야한다
```javascript
	var author = book.author;
	var name = author.surname;
	var title = book["main title"];
```
- 프로퍼티를 만들거나설정하는 것도 동일
```javascript
	book.edition = 6;
	book["main title"] = "ECMAScript";
```
- ECMAScript3에ㅓ는 마침표 연산자 다음에 오는 식별자로 예약어를 사용할 수 없다
- 만일 객체에 프로퍼티 이름으로 예약어를 사용하려하면 o["for"], o["class"]와 같이 []연산자를 사용해야한다

##6.2.1 연관배열로서의 객체
```javascript
	//다음의 두 표현식은 동일한 값을 갖는다
	object.property
	object["property"] //숫자나 문자열을 인덱스로 갖는 배열에 접근하는 형태와 유사. 이를 연관배열이라고한다
```
- 모든 자바스크립트 객체는 연관배열이다.
- 마침표 연산자로 프로퍼티에 접근할때는 프로퍼티의이름이 반드시 식별자여야한다
- 식별자는 데이터 타입이 아니므로 프로그램이 실행될 때 변경할 수 없다
- []연산자로 프로퍼티에 접근할 때는 프로퍼티의 이름이 문자열로 표현된다
- 문자열은 데이터타입이므로 중간에 변경될 수 있다
```javascript
	var addr="";
	for(i=0; i<4; i++) {
		addr += customer["address" + i] + "\n";
	}
```
- 위 코드는 address0, address1, address2, address3프로퍼티 값을 읽고 읽은 값을 addr변수에 차례로 이어붙인다
```Javascript
	function addstock(portfolio, stockname, shares) {
		portfolio[stockname] = shares;
	}

	function getvalue(portfolio) {
		var total = 0.0;
		for(stock in portfolio) { //portfolio의 각 주식에대해
			var shares = portfolio[stock]; //보유량과
			var price = getquote(stock); //주당 가격 얻어오고
			total += shares * price; //이둘을 곱한 가격을 누적해
		}
		return total; //총액을 반환
	}
```

##6.2.2 상속
- 객체는 고유 프로퍼티들을 가지고있고 동시에 해당 객체의 프로토타입 객체로부터 여러 프로퍼티들을 상속받는다
- 객체 o에서 프로퍼티 x를 찾는다면, 객체 o가 프로퍼티 x를 갖지 않으면 o의 프로토타입 객체에서 x를 찾는다
- 이 작업은 프로퍼티x를 찾거나 해당 객체 또는 객체의 프로토타입 객체가 null이 될때까지 계속된다
- 이처럼 객체의 프로토타입 속성은 특정 프로퍼티가 어떤 객체에 속해있는지 알 수 있는 프로퍼티 체인 또는 연결리스트를 생성한다
```javascript
	var o = {} //o는 Object.prototype을 상속받은 객체
	o.x = 1; //고유프로퍼티 x를 갖는다 
	var p = inherit(o); //p는 o와 Object.prototype을 상속받은 객체다
	p.y = 2; //고유프로퍼티 y를 갖는다 
	var q = inherit(p); //q는 p와 o, Object.prototype을 상속받은 객체다
	q.z = 3; //고유프로퍼티 z를 갖는다 
	var s = q.toString(); //q는 Object.prototype을 상속받은 객체이므로 toString()을 사용할 수 있다 

	q.x + q.y //q의 프로퍼티 x와 y는 o와 p에서 상속받았다
```
- 객체 o의 프로퍼티x에 값을 설정해보자
- 상속받지 않은 고유의 프로퍼티x를 갖고있을 경우 기존의 프로퍼티 값을 단순히 바꿀 수 있다
- 프로퍼티x를 갖고있지 않은 경우, 프로퍼티x를 만든 후 값을 설정한다
- 기존에 상속받은 프로퍼티x값은 새로설정되는 값에 잠시 가려진다
- 객체의 프로퍼티에값을 설정할 때는 프로토타입 체인을 검사한다
- 객체 o가 읽기 전용 프로퍼티 x를 상속하는 경우에는 해당 프로퍼티에 값을 설정할 수 없다
- 객체의 프로퍼티에 값을 설정할 수 있다면 기존 프로토타입 체인을 수정하지 않는다
- 객체에 해당 프로퍼티가 없다면 이를 만들고 값을 설정한다
- 객체에서 프로퍼티 값을 찾을 때 '상속이 발생한다'는 점은 중요한 특징 중 하나다!
```javascript
	var unitcircle = {r:1};
	var c = inherit(unitcircle); //객체 c는 unitcircle로 부터 프로퍼티 r을 상속받는다
	c.x = 1; c.y = 1; //객체c는 고유프로퍼티 x,y를 갖는다
	c.r = 2; //상속받은 r을 재정의한다
	unitcircle.r; //하지만 프로토타입객체의 프로퍼티r은 바뀌지 않는다
```
- 객체 o가 프로퍼티 x를 상위객체로부터 상속받았고 이 프로퍼티가 setter메서드를 가진 접근자 프로퍼티라고 가정하자
- 이때 객체 o의 프로퍼티 x에 값을 설정할때 객체 o에 새프로퍼티 x를 추가하지 않고, 상속받은 프로퍼티 x가 가진 setter메서드를 호출한다
- 하지만 setter메서드는 프로퍼티x 가 정의된 프로토타입 객체에서 호출되지 않고 객체o 에서 직접호출한다
- 따라서 setter메서드는 객체o에 임의로 프로퍼티를 정의할 수 있고 프로토타입체인도 변경하지 않는다

##6.2.3프로퍼티 접근 에러
- 