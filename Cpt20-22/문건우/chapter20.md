# 제 20장. strict mode

---

## strict mode란?

- strict mode는 ECMAScript 5에 추가된 새로운 기능으로, 자바스크립트 코드를 더 엄격히 검사하여 오류를 발생시킬 가능성이 있는 코드를 실행하는 것을 방지한다.
- strict mode는 전역의 선두 또는 함수 몸체의 선두에 `'use strict';`를 추가하여 적용한다.

```javascript
"use strict";

function foo() {
  x = 10; // ReferenceError: x is not defined
}

foo();
```

---

#### Strict mode가 필요한 이유 : 암묵적 전역

- strict mode를 사용하지 않으면 변수를 선언하지 않고 값을 할당하면 자바스크립트 엔진은 암묵적으로 전역 변수를 선언한다.

```javascript
function foo() {
  x = 10;
}

foo();

console.log(x); // 10
```

- 프로젝트 진행시 오류가 될 가능성이 크다.
