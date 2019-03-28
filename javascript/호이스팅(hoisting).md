# 호이스팅(Hoisting)
node.js 공부하다가 ES2015+ 문법 공부하다가 promise 전에 callback function 먼저 공부하다가 호이스팅까지 왔다.

## 호이스팅이란?
hoisting의 사전적 의미는 *끌어올리다*이다. 이 의미를 그대로 받아들이면 된다. 코드 라인이 1인 곳이 높은 곳이고, 라인 숫자가 큰 줄이 낮은 곳이라면 낮은 곳에서 높은 곳으로 끌어올리는 것이다. 그런데 무엇을 어디로 끌어올린다는 것일까?
* 무엇을? - 변수의 선언( ~~할당~~ ), 선언적 함수(~~함수 리터럴~~)
* 어디로? - 선언된 함수 내부 제일 위

## 호이스팅 대상
호이스팅되는 대상은 변수의 선언과 선언적 함수다. 

```javascript
console.log(someVar);  // undefined (에러가 아니다!)
var someVar = '할당하는 값'
```

```javascript
sayHello();  // hello
console.log(sayBye);  // undefined
sayBye();  // Uncaught ReferenceError: sayBye is not defined


function sayHello() {
	console.log('hello');
}

var sayBye = () => {
	console.log('bye');
}
```

ES2015+ 문법의 화살표함수를 공부하면서 `this`의 사용에 의도가 없다면 이제 웬만하면 함수는 화살표함수로 선언해야겠다고 생각했다. 그런데 호이스팅때문이라도 일반적인 상황이라면 `function`으로 선언해야겠다.

## let, const는 호이스팅 안되는건가?
위의 코드에서 변수를 `var`로 선언한 것은 의도한 것이다. `let`, `const`로 선언하면 `undefined`가 출력 안되고 에러가 뜨기 때문이다.

```javascript
console.log(someVar);  // Uncaught ReferenceError: someVar is not defined
let someVar = 'something';
```

결과적으로 `let`, `const`는 호이스팅 안되는 것처럼 보이지만 실제는 호이스팅이 되고 TDZ(Temporal Dead Zone)이라는 것 때문에 그리 보이는 것 뿐이다.

아직 이에 대해서 완벽히 이해하지 못했다…

우선 ‘`let`, `const`는 호이스팅 안되는 것처럼 보인다’라고만 알아둬야겠다.
