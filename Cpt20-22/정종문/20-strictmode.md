
### 20.1 strict mode란?

- ECMAScript 5부터 추가된 기능으로, 자바스크립트 코드를 더 엄격하게 검사하는 기능이다.
- strict mode를 사용하면 더 많은 예외를 발생시키고, 더 많은 오류를 발견할 수 있다.

#### 암묵적 전역이란 ? 

- 변수를 선언하지 않고 값을 할당하면, 자바스크립트 엔진은 암묵적으로 전역 변수를 생성한다.


### use strict 사용법

- strict mode를 사용하려면, 코드 최상단에 `'use strict';`를 추가하면 된다.
- 함수 단위로 strict mode를 사용하려면, 함수 내부에 `'use strict';`를 추가하면 된다.

```javascript
function foo() {
  'use strict';
  // strict mode 사용
}
```

### 20.4 함수 단위로 strict mode 쓰는 것도 피하자


### 20.5 strict mode가 발생시키는 에러

1. 암묵적 전역 변수 생성 시 에러 발생
-> 선언하지 않은 변수에 값을 참조하면, ReferenceError가 발생한다.

2. 변수, 함수, 매개변수의 삭제 시 에러 발생
-> delete 연산자로 변수, 함수, 매개변수를 삭제하면, SyntaxError가 발생한다.

3. 매개변수 이름 중복 시 에러 발생
-> 중복된 매개변수 이름을 사용하면, SyntaxError가 발생한다.

4. with 문 사용 시 에러 발생
-> with 문을 사용하면, SyntaxError가 발생한다. 
whit문? 이건뭔데? => with문은 객체의 속성에 접근할 때, 객체 이름을 반복하지 않아도 되게 해주는 문법이다. 하지만 with문은 사용하지 않는 것이 좋다. 왜냐하면 with문을 사용하면, 가독성이 떨어지고, 성능이 떨어지기 때문이다.

### 20.6 strict mode의 적용에 의한 변화

1. 일반 함수의 this
- strict mode에서 함수를 호출할 때, this에 undefined가 바인딩된다.

2. arguments 객체
- strict mode에서 arguments 객체의 요소를 수정하면, 해당 매개변수의 값도 수정된다.
```
(function (a) {
  "use strict";
  a = 2;
  console.log(arguments); // [ARGUMENTS] { '0': 4 }
})(4);

(function (a) {
  a = 2;
  console.log(arguments);   // [ARGUMENTS] { '0': 2 }
})(4);
```


### 요약

1. 엄격한 문법 체크
