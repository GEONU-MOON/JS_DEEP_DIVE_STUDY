## 15장 let, const 키워드와 블록 레벨 스코프

### 15.1 var 키워드로 선언한 변수의 문제점

- 변수 중복 선언 허용

```javascript
var x = 1;
var y = 1;

var x = 100; // var 키워드로 선언된 변수는 같은 스코프 내에서 중복 선언 허용
var y; // 초기화문이 없는 변수 선언문은 무시

console.log(x); // 100
console.log(y); // 1
```

- 함수 레벨 스코프

  함수 외부에서 var 키워드로 선언한 변수는 코드 블록 내에서 선언해도 모두 전역 변수

- 변수 호이스팅

  할당문 이전에 변수를 참조하면 언제나 undefined 반환

<hr>

### 15.2 let 키워드

- 변수 중복 선언 금지

  let 키워드로 이름이 같은 변수를 중복 선언하면 문법 에러 발생

- 블록 레벨 스코프

  모든 코드 블록을 지역 스코프로 인정

- 변수 호이스팅

  let 키워드로 선언한 변수는 변수 호이스팅이 발생하지 않는 것처럼 동작

  ➡️ 변수 선언문 이전에 참조하면 참조 에러(ReferenceError) 발생

  ```javascript
  console.log(foo); // undefined

  var foo;
  console.log(foo); // undefined

  foo = 1;
  console.log(foo); // 1
  ```

  - let 키워드로 선언한 변수는 **선언 단계**와 **초기화 단계**가 분리되어 진행

  - **TDZ(Temporal Dead Zone)**: 스코프 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간 (초기화 이전의 일시적 사각지대에서는 변수를 참조할 수 없다.)

  ```javascript
  let foo = 1;

  {
    console.log(foo); // ReferenceError: Cannot access 'foo' before initialization
    let foo = 2;
  }
  ```

  - let 키워드로 선언한 변수도 여전히 호이스팅 발생

- 전역 객체와 let

  - var 키워드로 선언한 전역 변수와 전역 함수는 전역 객체 window의 프로퍼티가 된다.

  - let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.

<hr>

### 15.3 const 키워드

상수를 선언하기 위해 사용

- 선언과 초기화

  - const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화를 해야 한다.

- 재할당 금지

- 상수

  - 상수는 재할당이 금지된 변수

- const 키워드와 객체

  - const로 선언된 변수에 객체를 할당한 경우 값 변경 가능

    _원시값은 변경할 수 없지만 객체는 변경 가능한 값이므로 변경이 가능하다._

**const 키워드는 재할당을 금지할 뿐 "불변"을 의미하지는 않는다.**

<hr>

### 15.4 var vs. let vs. const

- 변수 선언에는 기본적으로 const 사용

- let은 재할당이 필요한 경우에 사용

- ES6을 사용한다면 var 키워드는 사용 X

<hr>
