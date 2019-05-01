# 모듈(module)
## 파이썬 vs 노드
파이썬에서 `.py`파일은 당연히 모듈이다. 그래서 별다른 설정 없이 다른 파일에서 import 할 수 있다. 하지만 노드에서는 `.js`파일이 자동으로 모듈화되지 않는다. 모듈로 만들겠다는 명령어를 써줘야 한다.

* 파이썬
	* export: 모든 파일 또는 폴더는 자동으로 모듈화 또는 패키징된다.
	* import: 현재 파일에서 다른 경로에 있는 모든 파일을 자유롭게 사용할 수 있다.
* 노드
	* export: 현재 파일을 모듈화하겠다는 명령을 해줘야 한다.
	* import: 추출(export)된 모듈을 사용할 수 있다. 

## 노드 vs 자바스크립트(CommonJS vs ES6)
node.js는 언어의 개념이라기 보다는, 브라우저와 비슷한 위치의 것이라고 보면 된다. 자바스크립트가 브라우저 위에서 돌아가듯이 노드라는 환경에서 작동될 수 있는 것이다. 따라서 모듈 관련 문법의 차이를 얘기하기 위해서 노드와 자바스크립트를 대립시키는 것보다 CommonJS와 ES6를 대립시키는 것이 보다 정확하다.

ES6가 등장하기 전, 노드 환경에서 모듈을 사용하기 위해 CommonJS에서 모듈 기능을 구현했다. 그러다가 자바스크립트 문법 자체에서 모듈을 지원하기 시작했다. 따라서 다음과 같이 생각해야 한다.

> 노드 환경에서 모듈 기능을 사용하기 위해서는 CommonJS 문법을 사용

> 브라우저 환경에서 자바스크립트 자체 문법을 이용해 모듈 기능을 사용하기 위해서는 ES6 문법 사용.

* 노드(CommonJS)
	* 모듈 추출: `module.exports` 또는 `exports`
	* 모듈 사용: `require`
	* CommonJS의 문법을 사용한다. ES6가 등장하기 전에 사용하던 것이다.
* 자바스크립트(ES6)
	* 모듈 추출: `export default`
	* 모듈 사용: `import ... from ...`
	* babel과 같은 컴파일러와 함께 사용한다.

## module.exports vs exports
### module 객체
우선 `module`객체란 무엇인지 알아보자. [node.js 공식 api 문서](https://nodejs.org/api/modules.html#modules_the_module_object)를 보면 '**현재 모듈을 참조하는 변수**'라고 설명돼있다. 그리고 `module`객체는 global하지 않고 오히려 각 모듈에 대해 local하다.

> `module`객체는 현재 파일이다.

### module 객체 내의 exports 객체
현재 파일에서 추출(export)하고 싶은 것을 `module.exports`객체에 담는다. [공식문서](https://nodejs.org/api/modules.html#modules_module_exports) 에는 정확히 이렇게 표현돼있다.

> *assign the desired export object to module.exports.*

그러니까 `module.exports = something`이라는 구문이 있으면 이렇게 해석하면 된다. somethig이 어떤 것인가에 따라 나눴을 때

```javascript
const num = 1;

module.exports = num; // 현재 파일에서 1이라는 숫자를 추출하려는구나
```

```javascript
const str = 'hello';

module.exports = str; // 현재 파일에서 'hello'라는 문자를 추출하고 싶은거구나
```

```javascript
const obj = {
	num = 1,
	str = 'hello'
}

module.exports = obj; // 현재 파일에서 obj 객체를 추출했구나
```

### exports 객체
`exports`객체는 `module.exports`객체와 엄연히 다른 것이다. 다만 `exports`객체가 `module.exports`객체를 참조하고 있을 뿐이다. `exports`는 편의를 위해 만들어둔 것이다. 따라서 둘을 혼용할 수 있다.  그런데 혼동해서는 안되는 부분이 있다. `exports`객체는 주소를 담고 있는 변수고 `module.exports`객체는 값을 담고 있는 변수라는 것이다.

>  `exports`객체는 주소를 담고 있고 `module.exports`객체는 값을 담고 있다.

이러한 차이로 나타날 수 있는 현상을 아래의 자료에서 볼 수 있다. 한 번 참고해보자
* [자료1](https://programmingsummaries.tistory.com/340) 
* [자료2](https://appletree.or.kr/blog/web-development/javascript/%ED%98%BC%EB%8F%99%ED%95%98%EA%B8%B0-%EC%89%AC%EC%9A%B4-module-exports%EC%99%80-exports%EC%9D%98-%EC%B0%A8%EC%9D%B4/) 
