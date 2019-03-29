# Promise와 비동기 처리
`Promise`에 대해 잘 설명한 문서 두 가지
* [블로그](ㄴ): 이해하기 쉽게 의미를 풀어 쓴 글
* [MDN web docs](ㅇ): 한 단어씩 의미를 곱씹어보며 읽으면 거의 완벽한 설명임을 느낄 수 있다.

## Promise란?
```javascript
new Promise(execution)

new Promise((resolve, reject) => {
	// 비동기 작업
}
```
프로미스는 이렇게 만들 수 있다. `execution`은 실행함수로 `resolve`, `reject` 두 개의 함수 인자를 가지고 있고,  비동기 처리를 할 코드가 담겨 있다. 비동기 처리가 완료되면 처리 결과를 인수로 갖는 `resolve`함수를 호출하면 되고 비동기 처리에 실패하면 에러 메시지 등을 인수로 갖는 `reject`함수를 호출하면 된다.

## Promise의 세 가지 상태
* Pending(대기): 비동기 처리 작업 중, Promise객체가 호출되고 resolve 또는 reject가 호출되기 전까지의 상태
* Fulfilled(이행): 비동기 작업이 성공적으로 완료된 상태, `resolve`가 호출된 상태
* Rejected(실패): 비동기 작업이 실패한 상태, `reject`가 호출된 상태

## Promise를 이용한 비동기 처리
> ES5식 비동기 처리
```javascript
function afterAsync() {
	console.log('비동기 처리 후 뭔가 하기');
}

function asyncWork(callbackFunc) {
	console.log('비동기 처리 시작');
	setTimeout(callbackFunc, 1000);
}

asyncWork(afterAsync);
console.log('다른 일 먼저 하고 있기');
// 비동기 처리 시작
// 다른 일 먼저 하고 있기
// 비동기 처리 후 뭔가 하기
```

> Promise를 활용한 비동기 처리
```javascript
const afterAsync = () => {
	console.log('비동기 처리 후 뭔가 하기');
}

const asyncWork = () => {
	return new Promise((resolve) => {
		console.log('비동기 처리 시작');
		setTimeout(resolve, 1000);
	});
}

asyncWork().then(afterAsync);
console.log('다른 일 먼저 하고 있기');
// 비동기 처리 시작
// 다른 일 먼저 하고 있기
// 비동기 처리 후 뭔가 하기
```
