# 콜백함수(callback function)와 비동기 프로그래밍(asynchronous programming)
자바스크립트는 비동기 프로그래밍을 한다. 비동기 프로그래밍을 하는 방법은 세 가지가 있다. 
* 콜백함수(callback function)
* promise
* async/await

여기서는 콜백함수를 이용한 비동기 프로그래밍을 알아본다.

## 콜백(callback)이란?
[위키백과](ㅅ)설명에 따르면 콜백은 다른 코드의 인수로서 넘겨주는 실행 가능한 코드를 말한다. 콜백을 넘겨받는 코드는 이 콜백을 필요에 따라 즉시 실행할 수도 있고, 아니면 나중에 실행할 수도 있다.

여기에서 알 수 있듯이 콜백 자체는 비동기 프로그래밍과 반드시 연관되는 것은 아니다. `array.filter(callback)`에 사용되는 callback 함수는 비동기 방식과 관련이 없다. 

하지만 반대로 ES5에서 비동기 프로그래밍을 하기 위해서는 콜백함수를 반드시 사용해야 한다.

## 콜백함수를 이용한 비동기 프로그래밍
자바스크립트는 싱글쓰레드이기 때문에 비동기 방식으로 시간적 이득을 얻으려면 처리하려는 작업을 다른 자원에게 위임해줘야한다. 그래서 주로 I/O 작업에서 비동기 처리를 한다. I/O작업은 파일 다운로드, 데이터베이스 접근, 서버 통신 등이 있다.

비동기 작업 후 무슨 일을 할 지 콜백을 통해 전달한다. 예를 들어 서버 통신 후 성공했을 경우 실행할 콜백과, 실패했을 때 실행할 콜백 총 두 개를 인수로 전달해줄 수 있다.

> 잘못된 예시
```javascript
function getData() {
	let data;
	$.get('url', (response)=>{
		data = response;
	});
	console.log(data);
}

getData();  // undefined
```

> 옳은 예시
```javascript
function getData(callback) {
	$.get('url', callback(response));
}

getData((response)=>{
	console.log(response);
});
```

## 콜백헬(callback hell)
콜백함수를 중첩으로 계속 쓰면 콜백헬(callback hell)이라고 불리는 코드가 만들어진다. 이와 관련해 많은 도움을 받은 [웹문서](ㅇ)를 남겨놓는다. 

promise, async/await 방식을 쓰지 않고 콜백헬을 극복하는 방법도 소개되었다.

