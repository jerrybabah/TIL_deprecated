# vue-cli
## vue-cli란 무엇인가

 [vue-cli](https://cli.vuejs.org/)  공식 문서에 보면 이렇게 소개돼있다.
> Standard Tooling for Vue.js Development

vue-cli는 vue.js 개발을 위한 표준 도구이다. 되게 포괄적인 의미를 담고 있다. 도구이긴 한데 어떤 도구일까?

먼저 vue.js 어플리케이션 개발을 위해서 vue 자체 기능 말고 추가로 필요한 것을 생각해보자. 라우팅을 도와주는 vue-router, 상태관리를 해주는 vuex가 있을 수 있고, webpack과 같은 빌딩 도구도 있다. vue-cli는 이것들을 하나하나 설치해가며 관리하기 번거로우니 통합적으로 관리해주는 도구라고 생각하면 될 것 같다.
> vue-cli는 typescript, vue-router, vuex, linter, webpack 등을 통합적으로 관리해주는 도구   

## vue-cli가 하는 것
1. 라이브러리 설치: linter, vuex 등
2. 스캐폴딩: 디렉토리 구조 생성
3. 설정: babel, eslint 등의 설정
4. 빌드: webpack

(gulp, grunt, browserify), (webpack), (vue-cli) 순으로 기능이 통합되고 상위의 개념이라고 보면 된다.
