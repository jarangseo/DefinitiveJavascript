
#5장 구문
- 표현식은 어떤 값을 생성하기 위해, 구문은 어떤 일을 하기 위해 실행된다
- 문장은 마침표(.)로 끝나고 구문은 세미콜론(;)으로 끝난다
- 자바스크립트 프로그램은 순서대로 실행되는 세미콜론으로 끝나는 구문들의집합이다
- 조건은 if와 switch처럼 자바스크립트 인터프리터가 표현식의 값에 따라 구문을 실행하거나 건너뛸 수 있는 구문
- 루프는 while이나 for처럼 구문들을 반복 실행하는 구문
- 점프는 break, return,throw처럼 인터프리터가 프로그램의 특정부분으로 건너뛸 수 있게 해주는 구문

##5.1 표현문
- 구문 중 가장 간단한 형태는 부수 효과가 있는 표현식
- ex) 할당문
```javascript
  greeting = "Hello " + name;
  i += 3;
```
- ex) ++, -- : 변수 값 자체를 바꾸는 부수효과, 변수에 값을 할당한듯한 효과
```javascript
  counter++;
```
- ex) delete : 객체프로퍼티를 삭제, 표현식의 일부로 쓰이기 보다는 구문으로 많이 쓰인다
```javascript
  counter++;
```
- 클라이언트 측 함수호출은 표현식이지만 웹브라우저에 영향을 주기도 한다
- 함수가 부수효과가 없다면 함수가 표현식의 일부거나, 할당문의 일부가 아닌 이상 호출하는 의미가 없다
- Math.cos(x)의 경우, 결과를 그냥 버리지 않고 변수에 담아두었다가 사용해야 의미가 있다.

##5.2 복합문과 빈 구문
- 하나의 표현식 안에 여러 표현식을 함칠때 쉼표연산자를 사용
- 구문블록은 단 순히 여러구문을 중괄호로 감싼다
- 그래서 아래의 예는 단일 구문처럼 동작
```javascript
  x = Math.PI;
  cx = Math.cos(x);
  console.log("cos(ㅠ) = " + cx);
```
- 구문블록에 대해 알아야 할것
- 1. 세미콜론(;)으로 끝나지 않는다
- 2. 블록 안의 구문은, {}를 기준으로 들여쓰기한다
- 3. 자바스크립트는 블록단위 유효범위(scope)가 존재하지 않는다. 
- 그러므로 블록 안에 선언된 변수는 블록 뿐 아니라 블록 밖에서도 접근할 수 있다
- 빈 구문 : 하나의 구문이 있어야할 곳에 아무런 구문도 없는 것이다
```javascript
  ; //이게 빈 구문, 아무것도 실행하지 않는다
  
  //아래와 같은 몸체가 비어있는 루프를 만들때 유용
  for(i=0; i<a.length; a[i++] = 0) /*비어있음 empty*/ ; 
  //코드에 고의로 빈 구문을 사용했다는 것을 주석으로 써둘 것
  //위 루프에서 a[i++]=0표현식으로 배열이 초기화되므로 별도의 루포 몸체가 필요없다
  //자바스크립트 문법은 루프 몸체에 구문을 반드시 사용해야하므로 빈 구문을 사용했다
  
  if((a==0) || (b==0)); //실수로 if문 뒤에 세미콜론 넣으면, 빈 구문으로 인식하여 아무 일도 하지 않는다
    o = null; //이 행은 조건을 무시하고 항상 실행된다 
```

##5.3 선언문
- var와 function은 변수와 함수를 선언하는 선언문
- 변수나 함수 이름 같은 식별자를 정의한다

##5.3.1 var
- 하나 이상의 변수를 선언
```javascript
  var 변수_1 [ = 값_1 ] [ ,..., 변수_n [ = 값_n ]]
```
- 각 변수는 초기값 지정을 위해 표현식을 가질 수도 있다
```javascript
  var i;
  var j = 0; //초기값 0을위해 표현식 가짐
  var p,q;
  var greeting = "hello" + name;
  var x = 2.34, y = Math.cos(0.75), r, theta;
  var x = 2, y = x*x;
  var x = 2,
      f = function(x) { return x*x },
      y = f(x);
```

- 함수 내부에서 사용하는 var문은 지역변수로 정의되고, 함수 내에서만 사용할 수 있다
- var문이 최상위 코드로 사용되면, 전역변수로 선언된 거고 자바스크립트 프로그램 전역에 걸쳐 사용된다 
- 전역변수는 전역객체의 프로퍼티다
- 다른 전역프로퍼티와 달리var로 선언된 프로퍼티는 delete로 삭제할 수 없다
- var문에서 변수에 초기값을 지정하지 않으면 undefined가 초기값이 됨
- var문은 for문, for/in루프의 일부에 사용할 수 있다
- 이들 변수는 유효범위 최상단으로 끌어올려져(hoisted) 루프 밖에서 선언된 변수들 처럼 사용할 수 있다
```javascript
//같은 변수를 여러번 선언해도 무제될 것이 없다
  for(var i = 0; i < 10; i++) console.log(i);
  for(var i = 0, j = 10; i < 10; i++, j--) console.log(i*j);
  for(var i in o) console.log(i);
```
- 위의 코드와 아래의 코드 동일하게 동작함
```javascript
//같은 변수를 여러번 선언해도 무제될 것이 없다
  for(var i = 0; i < 10; i++) console.log(i);
  for(i = 0, j = 10; i < 10; i++, j--) console.log(i*j);
  for(i in o) console.log(i);
```

##5.3.2 function
- function키워드 : 함수를 정의하는데 사용
```javascript
  var f = function(x) { return x+1; } //변수에 함수를 할당하는 표현식
  function f(x) { return x+1; } //변수 이름을 포함한 구문
```
function 함수이름([전달인자1 [, 전달인자2 [..., 전달인자n]]) {
  구문
}
- '함수이름'은 정의할 함수 이름을 식별자로 갖는다
- 괄호 속에는 전달인자들이 쉼표로 구분되어 따라온다
- 함수 몸체는 하나 이상의 자바스크립트 구문들로 구성된다
- 이 구문들은 함수가 정의될때 실행되는 것이 아니다
- 실행될 수 있는 형태의 새로운 함수객체와 연결됐을때 실행된다
- 함수를 정의하는 몇가지 예
```javascript
  function hypotenuse(x,y) {
    return Math.sqrt(x*x, y*y); //return문
  }
  function factorial(n) { //재귀함수
    if(n <=1 ) return 1;
    return n * factorial(n-1);
  }
```
- 함수 선언문은 자바스크립트 최상위 단계에서 나타나거나 다른 함수 내에 중첩될 수 있다
- 다른함수 속에 중첩되었을 때는 중첩된 함수 내에서 최상위 단계에 위치하게 된다
- 함수 선언은 if문이나 while루프 또는 다른 구문 안에 있을 수 없다
- 함수선언구문과 함수정의표현식 모두 새 함수 객체를 만든다
- 함수선언 구문은 함수 이름을 포함, 함수 정의표현식은 포함하지 않는다
- 함수 선언문은 함수 이름을 변수로 선언한 후 이 변수에 함수 객체를 할당하고 스크립트나 함수 유효범위 최상위에 위치해 해당 유효범위 내에서 사용가능
- var문을 이용한 변수 선언은 유효범위 최상위에 위치하지만, 최초 변수를 초기화한 코드는 그대로 유지된다
- 하지만 함수 선언문은 함수이름과 본문 모두 최상단에 위치한다
- 즉 자바스크립트 함수 선언이 끝나기 전에 호출될 수 있다

##5.4 조건문
- 조건문은 두 개 이상의 경로로 코드를 분기, 인터프리터는 이 중 반드시 하나의 경로를 따른다

##5.4.1 if
- 첫번째 형태
```javascript
  if(표현식)
  구문
```

```javascript
  if( username == null ) //username이 null이거나 undefined면
    username = "John Doe";
```
- 위와 같은 구문
```javascript
if( !username ) //username이 null, undefined, false, 0, "" 또는 NaN일때
    username = "John Doe";
```
- 블록으로 여러 구문 하나로 묶기
```javascript
  if(!address) {
    address = "";
    message = "Please specify a mailing address.";
  }
```
- 두번째 형태
```javascript
  if(표현식)
    구문1
  else
    구문2
```
- 예
```javascript
  if( n == 1 )
    console.log("You have 1 new message.");
  else
    console.log("You have" + n + "new messages.");
```
- 중첩된 if문에서 else사용시 주의할것!
```javascript
  i = j = 1;
  k = 2;
  if(i == j)
    if(j == k)
      console.log("i equals k");
    else
      console.log("i doesn't equal j");//틀림!
```
- 자바스크립트 인터프리터의 해석은 아래와 같다 
```javascript
  if(i == j) {
    if(j == k)
      console.log("i equals k");
    else
      console.log("i doesn't equal j");
  }
```
- else는 가장 가까운 if문에 속한다
```javascript
  if(i == j) {
    if(j == k) {
      console.log("i equals k");
    }
  }
  else {
      console.log("i doesn't equal j");
  }
```
##5.4.2else if
- 고유의 구문은 아니지만 걍 쓴다
```javascript
  if ( n == 1 ) {
  }
  else if( n == 2 ) {
  }
  else if( n == 3 ) {
  }
  else {
  }
```
- 아래의 코드는 위의 코드와 같다
```javascript
  if( n == 1 ) {
  }
  else {
    if( n == 2 ){
    }
    else {
      if( n == 3) {
      }
      else {
      }
    }
  }
```

##5.4.3 switch
- 여러 if문에서 동일한 표현식이 반복되는 문제점을 해결
```javascript
switch(구문) {
  표현식
}

switch(n) {
  case 1:
    break;
  case 2:
    break;
  case 3:
    break;
  default:
    break;
}
```
- break문: 코드의 실행을 중지하고 switch문이나 루프의 끝으로 건너뛰는 역할
- case문 : 실해하련느 코드의 시작지점을 결정할 뿐 끝나는 지점을 결정하지 않음
- 함수 내에서 switch문을 사용할 때는 break문 대신 return문을 쓸 수도 있다
```javascript
  function convert(x) {
    switch(typeof x) {
      case 'number: //주어진 숫자를 16진수 정수로 변환
        return x.toString(16);
      case 'string': //문자열을 큰 따옴표로 묶어서 반남
        return '"' + x + '"';
      default: //이외의 타입은 문자열로 변환
        return String(x);
    }
  }
```
- 대응하는 case를 판별할때는 동등연산자 == 가 아닌 일치연산자 ===가 사용된다 
- case표현식 안에 함수 호출이나 값 할당 같이 부수효과를 일으키는 표현식 사용해서는 안된다
- 가장 안전한 방법은 상수 표현식만으로 제한하는 것이다
- default레이블은 switch구문 내 어디서든 사용 가능하지만 대부분 가장 마지막에 위치시킨다

##5.5루프
- 루프문은 분기 경로에서 일정 부분의 코드를 실행한 후 다시 해당 분기 경로로 되돌아간다
##5.5.1 while
- if문이 기본 분기문, while무니 기본 루프문
```javascript
  while( 표현식 )
    구문
```
- 표현식의 값이 true면 구문 이 실행된 후 표현식이 다시 평가된다
- 인터프리터는 while구문의 표현식이 false로 평가될 때까지 루프의 몸체를 반복
- while(true)구문을 사용해 무한루프를 만들 수 있따
- 루프문을 이용해 0부터 9까지 출력
```javascript
var count = 0;
while( count < 10 ) {
  console.log(count);
  count++;
}
```

##5.5.2 do/while
- 표현식이 테스트되는 시점이 처음이 아니라 마지막
- 적어도 한번은 루프의 몸체가 실행된다
```javascript
  do
    구문
  while(표현식);
  
  function printArray(a) {
    var len = a.length, i = 0;
    if( len == 0 ) {
      console.log("empty array");
    }
    else {
      do {
        console.log(a[i]);
      } while (++i < len);
    }
  }
```
- while루프와 달리 do루프틔 끝에는 세미콜론이 붙는다

##5.5.3 for
```javascript
  for(초기화 ; 테스트 ; 증가)
    구문
```
-위의 for문과 아래의 while문은 같다
```javascript
  초기화;
  while(테스트) {
    구문
    증가;
  }
```
- 루프 시작 전에 '초기화'가 있어야한다
- 초기화 자리에 var를 사용한 변수 선언문도 허용하므로 루프카운터 선언하는 동시에 초기화 가능
```javascript
  for(var count = 0; count < 10 ; count++)
    console.log(count);
  
  var i,j;
  for(i=0,j=10; i<10 ; i++, j--)
    sum += i*j;
```
- 루프변수가 반드시 숫자가 아니어도됨
```javascript
  function tail(o) { //링크드 리스트 마지막 객체 o를 반환한다
    for(; o.next; o = o.next)
      // o.next가 true로 평가되면 계속 순회한다
    return o;
  }
```
- for(;;)구문은 while(true)구문과 같은 무한루프 만든다

##5.5.4 for/in
- 날림.. 내머릿속에있기를

##5.6 점프문

##5.6.1 레이블

##5.6.2 break

##5.6.3 continue

##5.6.4 return

##5.6.5 throw
```javascript
  function factorial(x) {
    if(x<0) throw new Error("x must not be negative");
    for (var f =1 ; x > 1; f *= x, x--) /*비어있음 empty*/
    return f;
  }
  - 예외가 발생하면 정상적인 프로그램 실행을 중단하고 가까운 예외처리기로 이동
  - 예외처리기는  try/catch/finally 문 중에서 catch절을 사용해 작성한다
  
```

##5.6.6 try/catch/finally
```javascript
  try {
    
  }
  catch (e) {
  //try블록에서 예외가 발생한 경우 실행
  //지역변수e를 이용해 Error객체 또는 다른 값을 참조
  //이 블록에서는 예외를 처리하거나 무시
  }
  finally {
  //try블록과 관계없이 무조건실행되는 코드들이 위치
  }
  
  //finally문이 없는 try/catch문
  try {
    //사용자에게 입력할 번호를 물어본다
    var n = Number(prompt("Please enter a positive integer", ""));
    //입력한 숫자가 유효하면 factorial을 계산
    var f = factorial(n);
    alert(n + "! = " + f);
  }
  catch (ex) {//입력한 숫자가 유효하지 않다면
    alert(ex);
  }
```
  - finally문은 try블록이 일부라도 실행되면 무조건 실행된다
  - 만일 인터프리터가 return, continue, break문 등을 만나try블록에서 제어가 벗어날 경우 새 지점으로 이동하기 전에 finally블록이 실행된다 

##5.7 기타 구문

##5.7.1 with
- 변수의유효범위 체인을 밍시로 변경할 때 쓰인다
- with(객체) 구문
- with문을 사용하면 최적화하기 힘들고, 느리므로 가능한 사용하지 말자
```javascript
  //보통 html폼에서 어떤엘리먼트 접근 위해 다음과 같이 입력
  document.forms[0].address.value
  
  with(document.form[0]) { //with를 사용하면 form의 프로퍼티 이름 앞에 더이상 document.form[0]을 붙이지 않아도 된다
    //form엘리먼트에 직접 접근할 수 있다  
    name.value="";
    address.value="";
    email.value="";
  }
  
  //with문을 사용하지 않으면
  var f = document.forms[0];
  f.name.value = "":
  f.address.value = "";
  f.email.value = "";
  
  //객체 o가 프로퍼티 x를 갖고 있다면, 프로퍼티x의 값에 1을 할당한다
  with(o) x = 1;
  //객체o에 프로퍼티 x가 없다면 with문과 상관없이 x=1을 할당당
```
- with에 의해 추가된 임시객체는 일시적으로 유효범위 체인의 일부가 된다

