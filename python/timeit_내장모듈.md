# timeit 내장 모듈
```python  
import timeit

timeit.timeit(setup=‘pass’, stmt=‘pass’, number=1000000)
```

* setup: 측정하고 싶은 코드를 실행하기 전 실행되는 스크립트(임포트 할 것이 있으면 여기서 미리 해두면 된다.)
* stmt: 시간을 측정할 실행 코드
* number: 코드를 몇 번 실행시킬 지 정한다. 디폴트로 100만 번 실행한다.
