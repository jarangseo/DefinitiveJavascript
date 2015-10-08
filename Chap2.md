#2장 어휘구조
- `어휘구조`는 프로그램을 어떻게 작성해야 하는지를 알려주는 기본 규칙이다
- 가장 `저수준 문법`
- 변수 이름을 어떻게 작성해야 하는지와 어떤 문자를 주석으로 사용할지, 하나의 프로그램 구문이 다른 구문과 어떻게 구분이 되는지 살펴본다

##2.1문자집합
- 자바스크립트는 `Unicode문자집합`을 사용한다
- Unicode는 `ASCII나 Latin-1의 상위집합`이고 `대부분의 문자를 표현`할 수 있다
- `ECMAScript3표준`을 따르는 자바스크립트 구현체는 `Unicode2.1`이상을지원해야하고, `5표준`은 `3이상`을 지원해야한다

##2.1.1 대소문자 구분
- 자바스크립트는 `대소문자를 구분하는 언어`이다
- 키워드, 변수, 함수 이름, 식별자들은 모두 항상 대소문자를 구분해 입력해야 한다
- 그러나 `HTML은 대소문자를 구분하지 않는다`(XHML은 대소문자를 구분한다)

##2.1.2 공백, 개행, 제어문자
- 자바스크립트는 토큰들 사이에 있는 `공백들을 무시한다`
- 대부분의 경우, `줄바꿈 문자도 무시`(예외는 있다)
- 자바스크립트는 공백과 줄바꿈을 마음껏 사용할 수 있어서 깔끔하고 일관된 형태로 코드 형식을 변경하거나 들여쓰기할 수 있다
- 일반적인 `공백문자(\u0020), 탭(\u0009), 수직탭(\u000B), 폼 피드(\u000C), 줄 바꿈없는 공백(\u00A0), 바이트 수서 표식(\uFEFF), 유니코드 카테고리에 포함된 문자들`도 공백으로 인식
- `라인피드(\u000A), 캐리지 리턴(\u000D), 줄바꿈 문자(\u2028), 문단 구분자(\u2029)문자`를 줄바꿈으로 인식
- 캐리지 리턴과 라인피드는 `한 줄 짜리 줄바꿈 문자`로 취급
- 유니코드 형식 제어 문자 중에 `RIGHT TO LEFT표식`과 `LEFT TO RIGHT표식`은 텍스트 형식이 바뀔 때 `시각적인 효과`를 제어.
- `형식 제어 문자`는 일부 `비영어권 언어를 적절히 표시할 때 중요`, 보통 주석이나 문자열 리터럴 정규표현식 리터럴에 포함될 수 있음.
- 형식 제어 문자는 변수 이름 같은 식별자에는 사용할 수 없다
- 예외적으로 `ZERO WIDTH JOINER(\u200D)`와 `ZERO WIDTH NON-JOINER(\u200C)`는 식별자에 사용할 수 있지만 첫 글자로는 사용할 수 없다

##2.1.3 유니코드 이스케이프 시퀀스
- 일부 컴퓨터 하드웨어와 소프트웨어로는 특정 유니코드 글자들의 집합을 입력으로 받거나 화면에 표시할 수 없음.
- 이와 같은 경우에도 `프로그래머가 유니코드를 사용할 수 있도록` 자바스크립트에서는 `16비트 유니코드` 글자를 표현할 수 있는 일련의 `6자리 ASCII문자열 시퀀스`를 정의하고 있음.
- 유니코드 이스케이프 시퀀스는 `\u`로 시작하고 이어서 `16진수 숫자`(대소문자 구분 없이 A~F) 네개를 사용
- 유니코드 이스케이프는 `문자열 리터럴`이나 `정규 표현식 리터럴` 혹은 `식별자(키워드는 제외)`에서 사용할 수 있다
- `주석에서도 사용`할 수 있지만, 주석에서 사용할 경우 일반 ASCII글자로 취급되므로 유니코드로 해석하지 않는다

##2.1.4 유니코드 정규화
- 유니코드는 `한 문자를 인코딩하는 방법이 하나 이상`일 수 있다
- 텍스트 에디터에서는 같아보이지만 실제로 글자의 코드 값이 다르기 때문에 컴퓨터에서 다른 글자로 인식됨.

##2.2주석
- ‘//’를 이용하기와 ‘/*’와 ‘*/’사이의 텍스트

##2.3리터럴
- 프로그램에 직접 나타나는 데이터 값
```javascript
12 //숫자12
1.2 //숫자1.2
"hello world" //문자열
'Hi' //문자열
true //불리언값
false //불리언값
/javascript/gi //'정규표현식'리터럴(패턴 매칭용)
null //객체가 존재하지 않음
```

##2.4 식별자와 예약어
- `식별자`는 `이름`
- 자바스크립트에서 식별자는 변수나 함수에 이름을 붙이거나 코드 내 반복문에 레이블을 붙이는데 사용.
- `시작`은 `알파벳, 밑줄, 달러`.
- `이어지는 문자`는 `알파벳, 숫자, 밑줄, 달러.`
- 식별자의 첫 글자로 숫자를 허용하지 않는 이유는 `자바스크립트가 숫자와 식별자를 쉽게 구별하기 위함`

```javascript
i
my_variable_name
v13
_dummy
$str
```

- 이식성과 편집이 용이성을 이유로, 일반적으로 식별자에는 `아스키문자와 숫자`만 사용
- 하지만 자바스크립트에서는 `식별자로 유니코드 문자 집합에 속한 문자와 숫자를 포함시킬 수도 있다`
- ECMAScript표준은 식별자의 두 번째 글자부터 유니코드의 모호한 카테고리인 `Mn이나 Mc 혹은 Pc`에 속한 글자를 사용할 수 있도록 하고 있다
- 이를 이용해 변수이름을 비영어권 언어로 작성할 수 있고, 수학 기호를 사용할 수도 있다

##2.4.1 예약어
- 자바스크립트는 몇 가지 키워드들을 식별자로 예약하고 있다

```javascript
break		delete	function	return	typeof
case		do		if 			switch	var
catch		else 	in 			this 	void
continue	false	instanceof	throw	while
debugger	finally	new			true	with
default		for 	null		try
```

- ECMAScript5에서는 다음의 단어들을 예약하고 있다

```javascript
class	const	enum	export	extends	import	super
```

- 다음의 단어들은 식별자로 사용할 수 있지만 엄격한 모드(Strict Mode)에서는 예약어로 사용된다

```javascript
implements	let 	private		public	yield	interface	package		protected	static
```

- 엄격한 모드에서는 다음 식별자를 사용하는 것을 제한한다. 완전히 예약어는 아니지만 변수나 함수 혹은 매개변수 이름으로 사용할 수 없다

```javascript
arguments eval
```

- ECMAScript3에서는 모든 자바 언어의 키워드들을 예약해 놓았지만, ECMAScript5에서는 그렇지 않다.
- ECMAScript3구현체에서는 다음 키워드들을 식별자로 사용해선 안된다.

```javascript
abstract	double	goto		native		static
boolean		enum	implements	package		super
byte		export	import		private		synchronized
char		extends	int 		protected	throws
class		final 	interface	public		transient
const		float	long		short		volatile
```

- 자바스크립트는 다음과 같이 전역변수와 함수를 정의하고 있다

```javascript
arguments		encodeURI			Infinity	Number	 		RegExp
Array			encodeURIComponent	isFinite	Object 			String
Boolean 		Error				isNaN 		parseFloat		SyntaxError
Date			eval				JSON		parseInt		TypeError
decodeURI		EvalError			Math		RageError		undefined
decodeURIComponent	function 		NaN 		ReferenceError	URIError
```

##2.5 선택적인 세미콜론 사용
- 자바스크립트에서도 구문을 구분하기 위해 세미콜론을 사용한다
- 여러구문이 서로 다른 줄에 나타나는 경우 세미콜론을 생략할 수 있다
- 또한 프로그램의 끝이나 다음 토큰이 '}'일경우 세미콜론을 생략할 수 있다
- 다음의 코드에서 두 구문이 각각 다른 줄에 있으므로 첫 행의 세미콜론은 생략할 수 있다

```javascript
a = 3;
b = 4;
```
- 그러나 다음과 같이 작성된 경우는 세미콜론이 반드시 필요하다

```javascript
a = 3; b = 4;
```
- 항상 모든 줄바꿈 문자를 세미콜론으로 구분하지 않음.
- 세미콜론 없이 코드를 해석할 수 없는 경우에만 세미콜론을 줄바꿈으로 처리.
- 즉, 현재 구문 다음에 오는 공백이 아닌 문자를 해석할 수 없을 경우 세미콜론으로 줄바꿈을 처리한다

```javascript
Var a
a
=
3
console.log(a)
//자바스크립트는 위의 코드를 다음과 같이 해석 ==>	Var a; a=3; console.log(a);
```
- 첫 번째 줄바꿈을 세미콜론으로 취급하는데 이는 세미콜론 없이 var a a코드를 해석할 수 없기 때문이다
- 두 번째 'a'는 그 자체로 'a;'이 될 수 있지만 좀 더 긴 구문인 'a = 3;'으로 해석할 수 있으므로 세미콜론으로 취급하지 않는다
- 다음의 코드는 두가지 별개의 구문을 작성한 것 처럼 보인다

```javascript
var y = x + f
(a+b).toString()
```

- 하지만, 두 번째 행의 괄호때문에 함수 f의 호출처럼 해석될 수도 있다

```javascript
var y = x + f(a+b).toString();
```

- 이 경우 두 가지 별개의 구문으로 작동하게 하려면 명시적으로 세미콜론을 사용해야 한다
- 일반적으로, 구문의 시작이 (,[,/,+,-로 시작하면 자바스크립트 인터프리터가 이전 구문에 이어서 계속 해석하게 된다
- 의도치 않은 해석을 피하기 위해 구문의 시작부분에 방어적으로 세미콜론 사용하기도 한다

```javascript
var x = 0 //세미콜론이 생략됐다
;[x,x+1,x+2].forEach(console.log) //구문 앞에 넣은 방어적인 세미콜론이 이 구문과 위 구문을 구분하게 해준다
```

- 지금까지 자바스크립트에서 줄바꿈을 세미콜론으로 해석하는 규칙을 살펴봤다.
- 이 규칙에는 두가지 예외가 있다
- 첫번째 예외는 `return, break, continue` 문을 사용했을 경우다
- 줄바꿈이 return, break, continue 바로 다음에 오는 경우 줄바꿈을 세미콜론으로 인식
- `return, break, continue와 다음에 오는 키워드 사이에 줄바꿈을 하지 말아야한다`

```javascript
return
true;
//⇨	return; true;
```

- 두 번재 예외는 `++나 --연산자`가 포함된 경우다
- 이 연산자들을 후치 연산자로 사용할 경우 반드시 `적용되는 표현식과 동일한 줄`에 나타나야 한다
- 그렇지 않으면 줄바꿈은 무조건 세미콜론으로 해석되고, ++와 --는 줄바꿈 다음 구문의 전치 연산자로 해석된다
```javascript
x
++
y
```
- 위의 코드는 x++; y;로 해석되지 않고,  x; ++y;로 해석된다
