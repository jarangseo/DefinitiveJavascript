##1.2 클라이언트 측 자바스크립트
- 자세한 내용은 2부에서
- 클라이언트 측 자바스크립트 프로그래밍 기법의 기초를 심층 예제를 통해 빠르게 살펴보자
- 13장<웹브라우저와 자바스크립트>에서 배우게 될 가장 중요한 부분은 자바스크립트 코드를<script>태그를 통해 HTML파일에 내장할 수 있다는 점

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
