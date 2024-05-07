## 9장 타입 변환과 단축 평가

### 9.1 타입 변환이란?
- 명시적 타입변환
   - 개발자가 의도적으로 값의 타입을 변환
   - 타입 캐스팅(type casting)이라고도 한다.

- 암묵적 타입변환
   - 의도와 상관없이 자바스크립트 엔진에 의해 변환
   - 타입 강제 변환(type coercion)이라고도 한다.


---
### 9.2 암묵적 타입 변환
#### ____9.2.1 문자열 타입으로 변환
`+` 연산자를 사용하면 문자열 타입으로 변환된다. `+`연산자는 피연산자 중 하나 이상이 문자열이면 문자열 연결 연산자로 동작한다.
#### ____9.2.2 숫자 타입으로 변환
- 산술 연산자중 +제외한 연산자 -, *, /, % 를 사용하면 숫자 타입으로 변환된다.

- 비교 연산자도 숫자 타입으로 변환한다.

```
'1' > 0  // -> true
```
#### ____9.2.3 불리언 타입으로 변환
if문의 조건식은 불리언 타입으로 암묵적 타입 변환 한다.

---
### 9.3 명시적 타입 변환
표준 빌트인 생성자 함수(String, Number, Boolean)를 new연산자 없이 호출하는 방법 이 있고, 빌트인 메서드를 사용하는 방법이 있다.

#### ____9.3.1 문자열 타입으로 변환
- String 생성자 함수를 new 연산자 없이 호출하는 방법
- Object.prototype.toString 메서드를 사용하는 방법
- 문자열 연결 연산자를 이용하는 방법

```js
// 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
// 숫자 타입 => 문자열 타입
String(1);        // -> "1"
String(NaN);      // -> "NaN"
String(Infinity); // -> "Infinity"
// 불리언 타입 => 문자열 타입
String(true);     // -> "true"
String(false);    // -> "false"

// 2. Object.prototype.toString 메서드를 사용하는 방법
// 숫자 타입 => 문자열 타입
(1).toString();        // -> "1"
(NaN).toString();      // -> "NaN"
(Infinity).toString(); // -> "Infinity"
// 불리언 타입 => 문자열 타입
(true).toString();     // -> "true"
(false).toString();    // -> "false"

// 3. 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
1 + '';        // -> "1"
NaN + '';      // -> "NaN"
Infinity + ''; // -> "Infinity"
// 불리언 타입 => 문자열 타입
true + '';     // -> "true"
false + '';    // -> "false"
```

#### ____9.3.2 숫자 타입으로 변환

- Number 생성자 함수를 new연산자 없이 호출하는 방법
- parseInt, parseFloat 함수를 사용하는 방법(문자열만 숫자 타입으로 변환 가능)
- `+` 단항 산술 연산자를 이용하는 방법
- `*` 산술 연산자를 이용하는 방법

```js
 // 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 숫자 타입
Number('0');     // -> 0
Number('-1');    // -> -1
Number('10.53'); // -> 10.53
// 불리언 타입 => 숫자 타입
Number(true);    // -> 1
Number(false);   // -> 0

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
parseInt('0');       // -> 0
parseInt('-1');      // -> -1
parseFloat('10.53'); // -> 10.53

// 3. + 단항 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
+'0';     // -> 0
+'-1';    // -> -1
+'10.53'; // -> 10.53
// 불리언 타입 => 숫자 타입
+true;    // -> 1
+false;   // -> 0

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
'0' * 1;     // -> 0
'-1' * 1;    // -> -1
'10.53' * 1; // -> 10.53
// 불리언 타입 => 숫자 타입
true * 1;    // -> 1
false * 1;   // -> 0

```

#### ____9.3.3 불리언 타입으로 변환
- Boolean생성자 함수를 new연산자 없이 호출하는 방법
- !부정 논리 연산자를 두 번 사용하는 방법
```js
// 1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
Boolean('x');       // -> true
Boolean('');        // -> false
Boolean('false');   // -> true
// 숫자 타입 => 불리언 타입
Boolean(0);         // -> false
Boolean(1);         // -> true
Boolean(NaN);       // -> false
Boolean(Infinity);  // -> true
// null 타입 => 불리언 타입
Boolean(null);      // -> false
// undefined 타입 => 불리언 타입
Boolean(undefined); // -> false
// 객체 타입 => 불리언 타입
Boolean({});        // -> true
Boolean([]);        // -> true

// 2. ! 부정 논리 연산자를 두번 사용하는 방법
// 문자열 타입 => 불리언 타입
!!'x';       // -> true
!!'';        // -> false
!!'false';   // -> true
// 숫자 타입 => 불리언 타입
!!0;         // -> false
!!1;         // -> true
!!NaN;       // -> false
!!Infinity;  // -> true
// null 타입 => 불리언 타입
!!null;      // -> false
// undefined 타입 => 불리언 타입
!!undefined; // -> false
// 객체 타입 => 불리언 타입
!!{};        // -> true
!![];        // -> true
```

---
### 9.4 단축 평가

#### ____9.4.1 논리 연산자를 사용한 단축 평가
| 단축 평가 표현식    | 평가 결과              |
|------------------|----------------------|
| true \|\| anything | true                 |
| false \|\| anything | anything             |
| true && anything   | anything             |
| false && anything  | false                |


#### ____9.4.2 옵셔널 체이닝 연산자
- 옵셔널 체이닝(optional chaining) 연산자 ?.는 좌항의 피연산자가 null또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

- false로 평가되는 Falsy(false, undefined, 0, NaN, ' ')값이라도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.

#### ____9.4.3 null 병합 연산자
- null 병합(nullish coalescing)연산자 ??는 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

- 논리곱&&연산자와 동일하게 모든 좌항의 피연산자가 Falsy(false, undefined, 0, NaN, ' ')값인 경우 우항의 피연산자를 반환하여 예기치 않은 동작이 발생할 수 있다.

- 옵셔널 체이닝과 마찬가지로 null 병합 연산자 ??는 좌항의 피연산자가 false로 평가되는 Falsy(false, undefined, 0, NaN, ' ')값이라도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.
