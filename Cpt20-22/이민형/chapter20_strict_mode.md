## 20장 strict mode

### strict mode

- 자바스크립트의 언어와 문법을 더 엄격하게 적용하는 모드다.

- 자바스크립트 언어와 문법을 더 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다.

### strict mode 적용

전역의 선두 또는 함수 몸체 선두에 'use strict';를 추가하면 적용된다.

- strict mode는 즉시 실행 함수로 감싼 스크립트 단위로 적용하는 것이 바람직하다.

### strict mode가 발생시키는 에러

- 암묵적 전역

- 변수, 함수, 매개변수의 삭제

  delete 연산자로 변수, 함수, 매개변수를 삭제하면 SyntaxError가 발생한다.

- 매개변수 이름의 중복

- with 문의 사용

### strict mode 적용에 의한 변화

- 일반 함수의 this

  strict mode를 적용하면 일반 함수의 this에는 undefined가 바인딩된다.

- arguments 객체

  매개변수에 전달된 인수를 재할당해도 arguments 객체에 반영되지 않는다.
