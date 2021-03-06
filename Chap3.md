##3장 타입, 값, 변수
- 프로그래밍 언어로 다룰 수 있는 값의 종류를 데이터 타입이라고 한다
- 변수는 값에 대한 이름을 정의하고, 이 값을 이름으로 참조한다
- 자바스크립트에서 타입은 크게 원시타입과 객체타입으로 나뉜다
- 원시타입으로는 숫자, 텍스트의 나열(문자열), 불리언이 있다
- null과 undefined는 원시값이긴 하지만, 숫자, 문자열, 불리언 중 하나는 아니다
- null과 undefined는 하나의 형식으로 봐야하며 이 형식에는 오직 자기 자신만이 값으로 들어 있다
- 자바스크립트는 숫자, 문자열, 불리언, null, undefined 외에 객체라는 값을 가진다
- 객체는 이름과 값을 갖는 프로퍼티의 집합이다
- 값은 숫자나 문자열 같은 기본 데이터 타입 값이 될 수도 있고 객체와 같은 복합 데이터 타입이 될 수 있다
- 자바스크립트 객체는 순서가 없는 값들의 집합이며, 각 값에는 이름이 지정되어 있다
- 자바스크립트는 배열이라는 특별한 종류의 객체를 정의한다
- 배열은 순서가 있는 값들의 집합니다
- 각 값에는 번호(index)가 지정된다
- 자바스크립트는 또한 함수라는 특별한 종류의 객체를 정의한다
- 함수는 실행코드를 지니는 객체로서, 실행코드를 수행하고 계산된 값을 반환한다
- 함수의 중요한 점은 함수는 값이고, 자바스크립트 프로그램이 함수를 보통 객체처럼 다룰 수 있다는 점이다
- 새로 생성된 객체를(new 연산자를 이용하여) 초기화하기 위해 사용되는 함수는 `생성자함수`이다
- 생성자는 객체들의 클래스를 정의한다
- 객체는 생성자로 초기화되는 대상을 말한다
- 클래스는 객체 타입의 부분타입으로 생각할 수 있다
- 코어 자바스크립트에서는 Array, Function뿐만 아니라 Date클래스(날짜를 표현하는 객체를 정의), RegExp클래스(정규표현식을 표현하는 객체를 정의), Error클래스(문법과 런타임에러를 표현하는 객체를 정의)를 정의한다
- 자바스크립트 인터프리터는 메모리 관리를 위해 자동으로 가비지 컬렉션을 수행
- 프로그램이 필요할 때 객체를 생성할 수 있고, 프로그래머는 이 객체를 어떻게 해제할지 걱정할 필요 없다
- 인터프리터는 그 객체가 다시 사용되지 않을거라 판단되면 자동으로 메모리에서 해제한다
- 자바스크립트는 객체지향 언어이다
- 다양한 타입의 값을 다루는 전역 함수를 정의해두기보다, 어떤 값과 작동하는 메서드를 해당 타입 스스로 정의해둔다는 말이다
- 예를 들어 배별의 원소들을 정렬하기 위해 배열 a를 sort()함수에 인자로 전달하지 않고, a의 sort()메서드를 호출한다

```javascript
a.sort() //sort(a)의 객체지향 버전
```

- 자바스크립트 객체만이 메서드를 소유한다
- 하지만, 숫자, 문자열, 불리언 값은 메서드를 가진 것처럼 동작한다
- null과 undefined는 자바스크립트에서 유일하게 메서드를 가질 수 없는 값이다
- 원시타입과 객체타입은 메서드를 가진 타입과 그렇지 않은 타입으로, 수정가능한 타입과 수정할 수 없는 타입으로 나뉠 수 있다
- 예를 들어 숫자는 그 자체로 값이므로 수정할 수 없다
- 자바스크립트에서 문자열은 인덱스를 이용해 문자에 접근할 수 있지만 수정할 수는 없다
- 자바스크립트의 값은 타입 변환이 자유롭다
- 문자열을 인자로 받아 처리하는 프로그램에 숫자를 인자로 넘기면, 숫자를 자동으로 문자열로 변경한다
- 마찬가지로 불리언 값을 다루는 곳에 불리언이 아닌 값을 사용하면 자바스크립트는 적절하게 변경할 것이다
- 자바스크립트 변수들은 타입이 정해져 있지 않다
- 변수에 어떤 타입의 값도 할당할 수 있고, 나중에 같은 변수에 다른 타입의 값을 할당할 수 있다
- 자바스크립트는 어휘 유효범위를 사용한다
- 함수 밖에서 선언된 변수들은 전역변수고, 자바스크립트 프로그램 어디서든 사용할 수 있다
- 함수 안에서 선언된 변수들은 유효번위가 함수 영역이며, 오직 함수 안에서만 사용 가능하다

##3.1 숫자
- 자바스크립트는 다른 프로그래밍 언어들과 다르게 정수 값과 실수값을 구분하지 않는다
- 모든 숫자를 실수로 표현한다
- 자바스크립트는 숫자를 IEEE 754표준에서 정의한 64비트 실수 형태로 표현한다
- 배열 인덱싱이나 비트연산과 같은 특정한 연산은 32비트 정수로 수행한다
- 숫자는 변수에 할당하기도 하고, 있는 그대로 사용하기도 한다
- 이렇게 사용되는 숫자를 숫자리터럴 이라고 한다
- 첫 번째 숫자 왼편에 뺄셈기호(-)를 사용해 음수를 표현한다
- 이때 (-)는 단항부정 연산자이지 숫자 리터럴 문법은 아니다

##3.1.1 정수 리터럴
- 자바스크립트에서 10진수 정수는 숫자 시퀀스형태로 작성된다
```javascript
0
3
10000000
```
- 자바스크립트는 10진수 리터럴 이외에 16진수 값을 인식한다
- 16진수 리터럴은'0x'나 '0X'로 시작하고 16진수 숫자들이 뒤따른다
- 16진수 숫자는 0에서 9까지의 문자, 10에서 15까지를 표현하는 a(A)부터 f(F)까지의 문자 중 하나이다.

```javascript
0xff //15*16 + 15 = 255
0xCAFE911
```

- 일부 구현체에서는 정수 리터럴을 8진수로도 표현할 수 있지만, ECMAScript표준에서 8진수 표현을 지원하지 않는다
- 8진수 리터럴은 숫자 0으로 시작하고 0부터 7사이의 숫자 시퀀스가 뒤따르는 형태이다
```javascript
0377 // 3*64 + 7*8 + 7 = 255
```
- 자바스크립트 구현체에 따라 8진수 리터럴을 지원할 수 있고 하지 않을 수도 있으므로 0으로 시작하는 정수 리터럴은 절대로 사용하지 말아야 한다
- 리터럴이 8진수인지 10진수인지 사용자가 판단하기 힘들기 때문!
- ECMAScript5의 엄격한 모드(Strict Mode)에서는 8진수 리터럴을 명시적으로 금지하고 있다

##3.1.2 부동소수점과 리터럴
- 부동소수점 리터럴은 소수점을 가질 수 있다
- 실수를 표현하는 전통적인 문법을 사용한다
- 실수는 정수부분과 소수점, 소수점 이하 부분으로 표현한다
- 지수표기법으로 표현할 수 있다
- 문자 e(E)가 나오고 그 뒤에 덧셈 혹은 뺄셈, 마지막으로 정시 지수값이 따라온다
- 지수표기법으로 표현한 값은 실수에 10을 지수 횟수만큼 곱한 값을 나타낸다
- [digits][.digits][(e|E)[(+|-)]digits]

```javascript
3.14
2345.789
.33333333333333
6.02e23
1.4738223E-32
```

##3.1.3산술 연산
- 자바스크립트는 기본적인 산술 연산 뿐 아니라, 더 복잡한 수치 연산을 Math객체를 통해 지원한다
- Math 객체는 프로퍼티로 정의된 함수들과 상수들을 정의하고 있다
```javascript
Math.pow(2,53)
Math.round(.6)
Math.ceil(.6)
Math.floor(.6)
Math.abs(-5)
Math.max(x,y,z)
Math.min(x,y,z)
Math.random()
Math.PI
Math.E
Math.sqrt(3)
Math.pow(3,3)
Math.sin(0)
Math.log(10)
Math.log(100)/Math.LN10
Math.log(512)/Math.LN2
Math.exp(3)
```

- 자바스크립트에서 산술연산은 오버플로와 언더플로, 0으로 나누는 에러를발생시키지 않는다
- Infinity는 무한대, -Infinity는 음의 무한대이다
- 0으로 나누는 연산은 무한대 또는 음의 무한대를 반환
- 0을 0으로 나누면 NaN을 출력한다
- NaN은 무한대를 무한대로 나누는경우, 음수에 루트를 싀우는 경우, 숫자가 아닌 피연산자로 산술을 시도한 경우에 발생
- ECMAScript3에서 Infinity와 NaN은 읽고 쓰기가 가능한 값이고 값이 변할 수 있다
- ECMAScript5에서 Infinity와 NaN은 읽기 전용 값으로 정의한다
- Number객체에서는 Infinity와 NaN을 따로 상수로 정의한다
```javascript
Infinity //읽고 쓰기 가능한 변수로 Infinity로 초기화된다
Number.POSITIVE_INFINITY //infinity와 같은 값이지만 읽기 전용이다
1/0 //Infinity와 같은 값이다
Number.MAX_VALUE + 1 //역시 Infinity로 평가된다
Number.NEGATIVE_INFINITY //이 표현은 음의 무한대이다
-Infinity
-1/0
-Number.MAX_VALUE - 1
NaN //읽고 쓰기 가능한 변수로 NaN으로 초기화된다
Number.NaN // NaN과 같은 값을 갖지만 읽기 전용 프로퍼티다
0/0 //NaN으로 평가된다
Number.MIN_VALUE/2 //언더플로: 0으로 간주된다
-Number.MIN_VALUE/2 //음의 0으로 간주된다
-1/Infinity //이것 또한 음의 0으로 간주한다
-0

```
- NaN은 자신뿐만 아니라 다른값과 같은지 비교할 수 없다
- 즉, x == NaN문을 작성할 수 없다
- 대신에, x != x라고 작성해야 한다
- isNaN()함수는 인자가 NaN이거나, 문자열이나 객체처럼 숫자가 아니라면 참을 반환한다
- isFinite()함수는 인자가 NaN, Infiniy또는 -Infinity 이 외에 숫자라면 참을 반환한다
- 음의 0과 양의 0은 나눗셈을 할 때를 제외하고 거의 같다

```javascript
var zero = 0; //일반적인 0
var negz = -0; //음의 0
zero === negz; //true ->0과 음의 0은 같다
1/zero === 1/negx; //false ->무한대와 음의 무한대는 같지 않다
```

##3.1.4 이진 부동소수점과 반올림 오류
- 자바스크립트에서는 한정된 숫자만 부동소수점 형태로 표현할 수 있다
- 자바스크립트에서 실수 연산을 할 때 근사값으로 표현한다
- 자바스크립트에서 사용하는 IEEE-754부동소수점 표현방식은 1/2, 1/8, 1/1024 같은 분수를 정확히 표현할 수 있다
- 이진실수표현은 0.1과 같은 값을 정확하게 표현할 수 없다
- 자바스크립트에서 숫자는 높은 정밀도를 가지고 있어서 0.1에 근접한 근사치를 낼 수 있지만, 정확히 표현할 수는 없어서 문제이다
```javascript
var x = .3 - .2; // 0.3 - 0.2
var y = .2 - .1; // 0.2 - 0.1
x === y; //false
x === .1; //false 0.3 - 0.2는 0.1이 아니다
y === .1; //true 0.2 - 0.1은 0.1과 같다
```
- 이러한 현상의 이유는 반올림 오류때문이다
- 자바스크립트 언어의 결함이 아니라 이진 부동소수점 숫자를 사용하는 프로그래밍 언어에서 볼 수 있는 공통적인 현상이다
- 자바스크립트의 다음 버전은 이런 반올림 문제를 피하는 십진수타입을 지원할 것이다(다음버전이 나왔는지 확인할것)

##3.1.5 날짜와 시간
- 코어 자바스크립트는 날짜와 시간을 표현하는 객체를 생성하기 위해 Date()생성자를 제공한다
- Date객체는 간단한 날짜 계산을 하는 메서드를 제공한다
```javascript
var then = new Date(2010, 0, 1); //2010년 1월 1일
var later = new Date(2010, 0, 1, 17, 10, 30); //2010년 1월 1일 오후 5시 10분 30초
var now = new Date(); //현재 날짜와 시간
var elapsed = now - then; //밀리초로 날짜 계산
later.getFullYear() //2010
later.getMonth() //0(월은 0부터 시작한다)
later.getDate() //1(일은 1로 시작한다)
later.getDay() //5(0은 일요일, 5는 금요일)
later.getHours() //17(오후 다섯시)
later.getUTCHours() //시간대에 의존한 UTC시간
later.toString() //Fri Jan 01 2010 17:10:30 GMT+0900 (KST)
later.toUTCString() //Fri, 01 Jan 2010 08:10:30 GMT
later.toLocaleDateString() //2010. 1. 1.
later.toLocaleTimeString() //오후 5:10:30
later.toISOString() //2010-01-01T08:10:30.000Z
```

##3.2 텍스트
- 문자열은 16비트 값들의 연속적으로 나열된 것
- 각 문자는 수정할 수 없는 유니코드 문자로 표현된다
- 문자열의 길이 값은 16비트 수
- 자바스크립트에서 문자열(& 배열)은 0기반의 인덱싱을 사용
- 빈 문자열의 길이 값은 길이값이 0이다
- 자바스크립트는 문자 하나를 하나의 타입으로 제공하지 않는다
- 하나의 16비트 값을 표현하기 위해서는 길이가 1인 문자열을 사용하면된다

##3.2.1 문자열 리터럴
- 문자열은 작은따옴표로 둘러싸거나 큰따옴표로 둘러싸면된다
- 큰 따옴표는 작은따옴표로 둘러싸인 문자열에 포함될 수 있고, 작은따옴표는 큰 따옴표로 둘러싸인 문자열에 포함될 수 있다
```javascript
""
'testing'
"3.14"
'name="myform"'
"이 문자열은 \n두줄이다."
```
- ECMAScript3에서 문자열 리터럴은 한 줄로 작성해야 한다
- ECMAScript5에서 줄 끝에 역슬래시를 두면 한 줄을 여러줄로 작성할 수 있다
- 줄바꿈 문자는 문자시퀀스 \n이다
```javascript
"two\nlines" //한 줄이 두줄로 표현된다
"one\ //세 줄로 표현된 한 문자열. ECMAScript5에서만 가능하다
long\
line"
```
- 문자열에서 어포스트로피를 '이스케이프(escape)'시키기 위해서는 역슬래시(\)를 사용해야한다
- 자바스크립트와 HTML을 섞어서 사용할 때 자바스크립트에서 작은따옴표나 큰따옴표 중 하나를, HTML에서 나머지 하나를 사용하는게 좋다
```javascript
<button onclick="alert('Thank you')">Click Me</button>
```

##3.2.2 문자열 리터럴의 이스케이프 문자열
시퀀스 / 표현하는 문자
\0	/ 널문자
\b 	/ 역스페이스
\t 	/ 수평탭
\n 	/ 줄바꿈문자
\v 	/ 수직탭
\f 	/ 폼 피드
\r 	/ 캐리지 리턴
\" 	/ 큰따옴표
\' 	/ 작은따옴표
\\ 	/ 역슬래시
\x 	/ 두개의 16진수 숫자XX에 의해 지정되는 Latin-1문자
\u 	/ 네개의 16진수 숫자XXXX에 의해 지정되는 유니코드 문자

##3.2.3 문자열 다루기
- 숫자에 +연산자를 적용하면 숫자들이 더해진다
- 문자열에 적용하면 두번째 문자열을 첫번재 문자열에 이어붙인다
- 문자열을 다루는 다양한 메서드들
```javascript
var s = "hello, world"
s.charAt(0) //"h" 첫번째 문자
s.charAt(s.length-1) //"d" 마지막문자
s.substring(1,4) //"ell" 두번째, 세번째, 네번째 문자
s.slice(1,4) //"ell" 두번째, 세번째, 네번째 문자
s.slice(-3) //"rld" 마지막 세문자
s.indexOf("l") //2 문자 "l"이 위치한 첫번재 위치
s.lastIndexOf("l") //10 문자 "l"이 위치한 마지막 위치
s.indexOf("l",3) //3 세번째 문자 이후 문자 "l"이 등장하는 위치
s.split(", ") //["hello", "world"] 부분문자열로 나뉜다
s.replace("h", "H") //"Hello, world" h를 H로 바꾼다
s.toUpperCase() //"HELLO, WORLD"
```
- 자바스크립트에서 문자열은 변경되지 않는다
- replace()와 toUpperCase()같은 메서드는 기존 문자열을 변경하지 않고 새 문자열을 반환한다
- 즉 문자열 관련 메서드는 호출시이ㅔ 기존 문자열을 수정하지 않는다
- ECMAScript5에서 문자열은 읽기전용 배열처럼 취급될 수 있고, 대괄호 대신 charAt()메서드를 사용해 개별 문자(16비트값)에 접근할 수 있다

##3.2.4 패턴 매칭
- 자바스크립트는 문자패턴을 나타내는 객체를 생성하기 위해 RegExp()생성자를 정의한다
- 이런 패턴은 정규 표현식에 기술되어 있고, 자바스크립트는 정규 표현식을 위해 펄(Perl)구문을 채택한다
- 문자열과 RegExp객체는 모두 패턴매칭과 '검색 후 바꾸기'기능을 수행하는 메서드를 가지고 있다
- Date객체처럼 RegExp는 유용한 API를 가지고 있는 특별한 종류의 객체다.
- RegExp는 문자를 다루는 강력한 수단을 제공한다
- RegExp가 자바스크립트의 기본 데이터 타입은 아니지만, 자바스크립트는 정규식에 대한 리터럴 문법을 가지고 있고 이는 자바스크립트 프로그램으로 바로 해석될 수 있다
- 한 쌍의 슬래시 사이에 있는 문자열은 정규 표현식 리터럴을 구성한다
```javascript
/^HTML/ //문자열의 첫 부분에 문자 H T M L과 일치
/[1-9][0-9]*/ //0이 아닌 숫자와 일치, 아무 숫자나 뒤따라온다
/\bjavascript\b/i //"javascript"와 일치, 대소문자를 구분한다
```
- RegExp는 유용한 메서드들이 정의되어 있다
- 또한 문자열은 RegExp객체를 인자로 갖는 메서드들을 가지고 있다
```javascript
var text = "testing: 1,2,3"; //간단한 문자열
var pattern = /\d+/g //하나 이상의 모든 숫자와 일치
pattern.test(text) //true, 일치하는 문자열이 존재
text.search(pattern) //9 첫번째로 매치하는 문자열의 위치
text.match(pattern) //["1", "2", "3"] 일치된 항목을 배열에 보관
text.replace(pattern, "#"); //"testing:#,#,#"
text.split(/\D+/); //["","1","2","3"] 숫자가 아닌 문자(열)로 나눈다
```

##3.3불리언 값
- 불리언 값은 참/거짓, on/off, yes/no를 표현한다
- 불리언 값이 될 수 있는 표현식은 예약어인 true와 false중 하나의 값으로 평가된다
- 불리언 값은 자바스크립트 제어구조 내에서 사용한다
- if/else문은 불리언 값이 true인 경우 한 가지 동작을 수행하고, false인 경우 나머지 동작을 수행한다
```javascript
if (a == 4)
   b = b + 1;
else
   a = a + 1;
```
- 다음은 모두 불리언 false값으로 변한다
```javascript
undefined
null
0
-0
NaN
""
```
- 모든 객체(와 배열)을 포함해 모든 값은 불리언 값으로 변환되고 true처럼 동작한다
- false와 앞의 여섯 값들은 거짓으로 판정되고 그밖의 모든 값은 참으로 판정된다
```javascript
if (o !== null) //o가 null이 아닐때 실행
if(o) //o가 false혹은 거짓값(null이나 undefined)가 아니라면 실행
```
- 불리언 값에 사용되는 세가지 중요한 연산자가 있다
- &&연산자는 불리언 AND연산을 수행한다. 두 연산자가 참 일때 참으로 평가하고 그렇지 않으면 거짓으로 평가한다
- ||연산자는 불리언 OR연산을 수행한다. 두 피연산자 중 하나라도 참이면 참으로 평가하고 모두 거짓이면 거짓으로 평가한다
- 단항 !연산자는 불리언 NOT연산을 수행한다. 거짓이면 참으로, 참이면 거짓으로 평가한다
```javascript
if ((x === 0 && y === 0) || !(z === 0)) {
//x와 y는 둘 다 0이거나 z가 0이 아니다
}
```

## 3.4 null과 undefined
- typeof(null) === "object"
- undefined : 초기화 X, 존재하지 않는 객체의 프로퍼티나 배열의 원소에 접근하려고 할 경우
- typeof(undefined) === "undefined"
- null == undefined : true
- null === undefined : false

## 3.5 전역객체
- 전역객체의 프로퍼티는 자바스크립트 전역에서 사용할 수 있게 정의된 심벌
- 자바스크립트 인터프리터가 시작할때(웹브라우저가 새로운 페이지를 불러올때) 새로운 전역객체를 만들고 그 프로퍼티들을 초기화
- undefined, Infinity, NaN과 같은 전역 프로퍼티
- isNaN(), parseInt(), eval()과 같은 전역함수들
- Date(), RegExp(), String(), Object(), Array()같은 생성자 함수
- Math, JSON같은 전역 객체들
- 최상위 코드(함수의 부분이 아닌 코드)에서 전역 객체 참조 위해 키워드 this사용
- window객체는 브라우저에 포함된 모든 자바스크립트 코드를 위한 전역 객체
- window객체는 전역객체를 참조하는 this대신 사용
- 전역 변수를 선언하면 이 변수는 전역 객체의 프로퍼티가된다

## 3.6 레퍼객체
- 레퍼객체 : 문자열, 숫자 ,불리언의 프로퍼티에 접근하려 할때 생성되는 임시객체
- 프로퍼티의 값이 함수일 때 이 함수를 메서드라고 한다
- 객체 o의 메서드 m은 o.m()이렇게 호출
```javascript
   var s = "hello world!";
   var word = s.substring(s.indexOf(" ")+1, s.length);
```
- 문자열 s의 프로퍼티 참조하려고 할때 new String(s)를 호출한것처럼 문자열 값을 객체로 변환
- 이 객체는 문자열 메서드를 상속하고 프로퍼티를 사용하는데 사용
- 프로퍼티 참조가 해제되면 임시객체는 메모리에서 회수됨
- 숫자와 문자열은 임시객체가 Number()혹은 Boolean()생성자가 호출될 때 생성됨
- null과 undefined의 레퍼객체는 없음
```javascript
   var t = "test"; //문자열
   t.len = 4; //프로퍼티에 할당하고 바로 임시객체를 회수함
   var s = t.len; //그러므로 프로퍼티를 참조하면 undefined가 출력됨
```
- 문자열, 숫자, 불리언은 객체처럼 동작하지만 값을 할당하는 것은 지속되지 않는다
- 문자열, 숫자, 불리언의 프로퍼티가 읽기 전용, 새로운 프로퍼티를 정의할 수 없다, 일반 객체와 다르다는 것을 기억할 것
- 명시적으로 레퍼객체를 생성할 수도 있다.
```javascript
   var s = "test", n = 1, b = true;
   var S = new String(s); //string레퍼객체
   var N = new Number(n); //number레퍼객체
   var B = new Boolean(b); //boolean레퍼객체
   s == S; //true
   n == N; //true
   b == B; //true
   s === S; //false
   n === N; //false
   b === B; //false
```

##3.7 원시 타입과 참조 타입
- 원시타입(undefined, null, 불리언, 숫자, 문자열)은 본래 타입을 바꿀 수 없다
```javascript
   var s = "hello";
   s.toUpperCase(); //"HELLO"를 반환
   s; //"hello"를 반환, 원래 문자열은 바뀌지 않는다
```
- 원시타입은 값으로비교된다
- undefined, null, 불리언, 숫자는 두 값이 같은 값이 가지고 있다면 같다
- 문자열은 두 문자열의 길이가 같고 각 인덱스에 있는 문자들이 같으면 같다
- 객체는 값으로 비교되지 않는다
- 객체는 참조로 비교된다
- 같은 객체를 참조하면 같다
```javascript
   var o = {x:1}, p = {x:1};
   o === p; //false
   var a = [], b = [];
   a === b; //false
   
   var a = [];
   var b = a;
   a === b; //true
   b[0] = 1;
   a[0]; //1
   a === b;
```
- 객체를 변수에 할당하는 것은 참조를 할당하는 것
- 객체 혹은 배열의 새로운 복사본을 만드려면 명시적으로 객체의 프로퍼티 또는 배열의 원소를 복사해야한다
```javascript
   var a = ["1", "2", "3"];
   var b = [];
   for( var i = 0; i < a.length ; i++ ){
      b[i] = a[i];
   }
   
   //객체,배열을 비교할 때 프로퍼티나 원소를 비교해야한다
   function equalArray(a,b) {
      if ( a.length != b.length) return false;
      
      for( var i = 0; i<a.length ; i++ ){
         if( a[i] !== b[i] ) return false;
      }
      
      return true;
   }
```

##3.8 타입변환
- 자바스크립트는 타입에 매우 유연하다
```javascript
   10 + " objects" // "10 objects" 숫자 10이 문자열로 변환
   "7" * "4" // 28 두 문자열이 숫자로 변환
   var n = 1 - "x" // NaN 문자열 "x"를 숫자로 변환할 수 없다
   n + " objects" // "NaN objects" 위에서 n이 NaN인데 이 NaN은 문자열 "NaN"으로 변환됨
```
- 숫자로 파싱할 수 있는 문자열은 숫자로 반환
- 앞뒤공백은 허용, but 공백이나 숫자가 아님 누자들이 섞인 경우는 문자열에서 숫자로 변환시 NaN
- true는 1로 변환, false와 빈문자열""은 0으로 반환
- 원시타입은 String(), Number(), Boolean()생성자 호출함으로써 레퍼객체로 변환
- null과 undefined는 변환할 수 없다

##3.8.1 변환과 동등 비교
```javascript
   null == undefined // true
   "0" == 0 // true
   0 == false // true
   "0" == false // true
```
##3.8.2 명시적 변환
- Boolean(), Number(), String(), Object()를 사용하기
- null과 undefined를 제외한 모든 값은 toString()메서드를 가지고 있다
- 특정 자바스크립트 연산자는 암시적 타입변환을 수행
- +연산자의 피연산자가 문자열이면 다른 피연산자를 문자열로 변환
- 단항연산자 +는 피연산자를 숫자로 변환
- 단항연산자 !는 피연산자를 불리언으로 변환시키고 부정연산을 한다
```javascript
   x + "" //String(x)와 같다
   +x //Number(x)
   !!x //Boolean(x)
```
- number클래스의 toString()메서드에 2에서 36까지 기수를 전달할 수 있다. 디폴트는 10.
```javascript
   var n = 17;
   binary_string = n.toString(2); // "10001"
   octal_string = "0" + n.toString(8); //"021"
   hex_string = "0x" + n.toString(16); //0x11"
```
- number클래스는 숫자를 문자열로 변환하는 세가지 메서드를 제공
- 1. toFixed()메서드 : 소수점 이후에 정의된 수와 문자열로 숫자를 변환
- 2. toExponential()메서드 : 지수표기법을 사용해 소수점 앞에 숫자 하나와 소수점 뒤에 지정된 만큼의 자릿수를 놓는 방식
- 3. toPrecision()메서드 : 유효자릿수 숫자의 전체 정수 부분을 표시할 정도로 크지 않다면 지수 표기법을 사용

```javascript
   var n = 123456.789;
   n.toFixed(0); //"123457"
   n.toFixed(1); //"123456.8"
   n.toFixed(2); //"123456.79"
   n.toFixed(3); //"123456.789"
   n.toFixed(4); //"123456.7890"
   n.toFixed(5); //"123456.78900"
   n.toExponential(0); //"1e+5"
   n.toExponential(1); //"1.2e+5"
   n.toExponential(2); //"1.23e+5"
   n.toPrecision(10); //"123456.7890"
```
- Number()함수 : 10진수정수로만 동작하고 숫자리터럴의 일부가 아닌 문자를 허용하지 않는다
- parseInt(), parseFloat()함수 : 리터럴의 일부가 숫자가 아니어도 된다
- parseInt() : 정수로만 변환할 수 있다
- parseFloat() : 정수와 부동소수점 모두 변환할 수 있다
```javascript
   parseInt("3 blind mice"); //3
   parseFloat(" 3.14 meters"); //3.14
   parseInt("-12.34"); //-12
   parseInt("0xFF"); //255
   parseInt("0xff"); //255
   parseInt("-0xFF"); //-255
   parseFloat(".1"); //0.1
   parseInt("0.1"); //0
   parseInt(".1"); //NaN
   parseFloat("$72.47"); //NaN
   
   //parseInt()는 기수를 정의하는 인자를 받는다
   parseInt("11", 2); //3
   parseInt("ff", 16); //255
   parseInt("zz", 36); //1295
   parseInt("077", 8); //63
   parseInt("077", 10); //77
```

##3.8.3 객체에서 원시타입으로 변환
- 모든객체(배열과 함수, 레퍼객체를 포함)는 true로 변환한다
- new Boolean(false)는 원시타입이 아닌 객체이므로 true로 변환환
- 1. toString()메서드 : 문자열로 반환
- Array클래스의 toString()메서드 : 배열 원소를 문자열로 변환하고 원소들 사이에 쉼표를 삽입
- Function클래스의  toString()메서드 : 함수의 구현 부분을 반환
- Date클래스의 toString()메서드 : 사람이 읽을 수 있는 날짜와 시간 형태의 문자열 반환
- RegExp클래스의 toString()메서드 : RegExp리터럴처럼 보이는 문자열로 변환
```javascript
   ({x:1, y:2}).toString(); //"[object Object]"
   [1,2,3].toString(); //"1,2,3"
   (function(x) { f(x); }).toString(); //"function (x) { f(x); }"
   /\d+/g.toString(); //"/\d+/g"
   new Date(2010,0,1).toString(); //"Fri Jan 01 2010 00:00:00 GMT+0900 (KST)"
```
- 2.valueOf() : 대부분 객체 그 자신을 반환
- Date클래스의 valueOf()메서드 : 내부표현으로 된 날짜를 반환
```javascript
   var d = new Date(2010, 0, 1);
   d.valueOf(); //1262271600000
```

##3.9 변수선언
- 생략

##3.10 변수의 유효범위
- 유효범위 : 어떤 변수가 정의되어있는 영역
- 전역변수의 유효범위는 전역적, 지역변수의 유효범위는 지역적
```javascript
   var scope = "global"; // 전역변수
   function checkscope(){
      var scope = "local"; // 전역변수와 같은 이름으로 지역변수 선언
      return scope;
   }
   checkscope(); //"local"
```
- 전역 유효범위에서는 var사용하지 않고 전역변수를 선언가능
- 지역변수 선언을 위해서는 var를 사용해야한다
```javascript
   scope = "global"; //전역변수 선언
   
   function checkscope2() {
      scope = "local"; //전역변수를 바꿔버렸네!
      myscope = "local"; //암묵적으로 전역변수 선언
      return [scope, myscope]; //두변수의 값을 반환
   }
   
   checkscope2(); //["local","local"]:부작용 발견!
   scope; //"local":전역변수가 바꼈다!
   myscope; //"local":전역 네임스페이스가 혼란스럽다
```
- 각 함수에는 자신만의 유효범위가 있다
```javascript
   var scope = "global scope"; //전역변수 선언
   
   function checkscope() {
      var scope = "local scope"; //지역변수
      function nested(){
         var scope = "nested scope"; //함수안에 포함된 유효범위의 지역변수
         return scope; //nested()안의 변수를 반환
      }
      return nested(); //두변수의 값을 반환
   }
   
   checkscope(); //"nested scope"
```

##3.10.1 함수 유효범위와 끌어올림(Hoisting)
- 자바스크립트는 블록단위 유효범위를 지니지 않고, 함수 유효범위를 지닌다
```javascript
   function test(o) {
      var i = 0; //i는 함수 전체에걸쳐 정의된다
      if (typeof o == "object") {
         var j = 0; //j는 블록 뿐 아니라, 함수 전체에 걸쳐 정의된다 
            for(var k=0; k<10; k++) { //k는 반복문 외에도 함수 전체에 걸쳐 정의된다
               console.log(k); //0~9까지출력됨
            }
         console.log(k); //10
      }
      console.log(j); //undefined
   }
```
- 자바스크립트는 함수 안에 있는 모든 변수를 함수 맨 꼭대기로 '끌어올린'것처럼 동작한다
```javascript
var scope = "global";
function f() {
   console.log(scope); //undefined
   var scope = "local";
   console.log(scope); //local
}
```
- 위의 코드에서 함수 내 1행이 undefined로 출력된다
- 얘기 가리키는 scope는 2행에 보이는 지역변수 scope다
- 같은 이름의 지역변수에 의해 전역변수가 감춰진것
- 지역변수가 함수 전체에 걸쳐 정의되었더라도 var문이 실행되고 나서야 초기화되는데 1행에서는 아직 초기화가 안됐으니깐 undefined가 출력되는 것이다. 
- 위 코드는 아래의 코드와 같다

```javascript
var scope = "global";
function f() {
   var scope;
   console.log(scope); //scope변수가 존재하지만 아직 "undefined"값
   scope = "local"; //초기화됨
   console.log(scope); //local
}
```
- 아래의 코드같은 경우 함수 내에서 전역변수와 같은 이름의 지역변수가 선언되지 않았으므로 전역변수에 바로 접근한 것
```javascript
var scope = "global";
function f() {
   console.log(scope); //global
}
```

##3.10.2 프로퍼티로서의 변수
```javascript
   var truevar = 1; //올바르게 선언한 전역변수, 삭제할 수 없다
   fakevar = 2; //삭제가능한 전역객체의 프로퍼티를 만든다
   this.fakevar2 = 3; //삭제가능한 전역객체의 프로퍼티를 만든다
   delete truevar; //false
   delete fakevar; //true
   delete fakevar2; //true
```
- 자바스크립트 전역변수는 전역객체의 프로퍼티다

##3.10.3유효범위 체인
- 변수의 유효범위는 변수가 정의된 소스코드의집합
- 전역변수는 프로그램 전체에 걸쳐 정의됨
- 지역변수는 함수 내에서 전체에 걸쳐 정의되고, 중첩된 함수 내에서도 정의됨
- 자바스크립트의 모든 청크(전역 코드 또는 함수)는 그것과 연관된 유효범위 체인을 가지고 있다
- 최상위 자바스크립트 코드의 경우 단 하나의 전역객체만으로 이루어짐
- 중첩되지 않은 한 함수의 경우 유효범위 체인은 두개의 객체로 이루어짐
- 하나는 매개변수와 지역변수를 정의한 객체, 다른 하나는 전역객체
- 중첩된 함수는 세개 이상 객체를 갖는다
