## 9장 타입 변환과 단축 평가

### 9.1 타입 변환이란?

- 명시적 타입 변환(explicit coercion), 타입 캐스팅(type casting)

  의도적으로 타입을 변환한다.

```javascript
var x = 10;
var str = x.toString(); // 숫자를 문자열로 타입 캐스팅
```

- 암묵적 타입 변환(implicit coercion), 타입 강제 변환(type coercion)

  자바스크립트 엔진에 의해 암묵적으로 타입이 변환된다.

```javascript
var x = 10;
var str = x + "";
console.log(typeof str); // string
```

➡️ 명시적 타입 변환, 암묵적 타입 변환 둘다 기존 원시 값을 직접 변경하는 것은 아니다.

\*원시 값은 변경 불가능한 값

<hr>

### 9.2 암묵적 타입 변환

- 코드의 문맥에 부합하지 않는 상황에 자바스크립트는 가급적 에러를 발생시키지 않도록 암묵적 타입 변화를 통해 표현식을 평가한다.

#### \_\_9.2.1 문자열 타입으로 변환

```javascript
1 + '2' // '12'

// 심벌 타입
(Symbol()) + ''; // TypeError: Cannot convert a Symbol value to a string

// 객체 타입
({}) + '' // "[object Object]"
Math + '' // '[object Math]"
[] + '' // ""
[10, 20] + '' // "10,20"
(function(){}) + '' // "function(){}"
Array + '' // "function Array() { [native code] }"
```

#### \_\_9.2.2 숫자 타입으로 변환

```javascript
1 * "10"; // 10
1 / "one"; // NaN
```

- 비교 연산자는 피연산자의 크기를 비교하므로 모든 피연산자는 코드 문맥상 모두 숫자 타입이어야 한다.

```javascript
"1" > 0; // true
```

- \+ 단항 연산자

```javascript
+undefined + // NaN
+Symbol() + // TypeError: Cannot convert a Symbol value to a number
+{} + // NaN
+{} + // 0
+[10, 20] + // NaN
```

빈 문자열(''), 빈 배열([]), null, false는 0으로, true는 1로 변환된다.

```
+(function () {}); // NaN
```

#### \_\_9.2.3 불리언 타입으로 변환

_자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값(참으로 평가되는 값) 또는 Falsy 값(거짓으로 평가되는 값)으로 구분한다._

- false로 평가되는 값 (Falsy)
  - false
  - undefined
  - null
  - 0, -0
  - NaN
  - '' (빈 문자열)
- false 값 외에는 모두 true로 평가되는 Truthy 값

```javascript
// Truthy/Falsy 값 판별하는 함수
isTruthy();
isFalsy();
```

<hr>

### 9.3 명시적 타입 변환

#### \_\_9.3.1 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메서드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법

#### \_\_9.3.2 숫자 타입으로 변환

1. Number 생성자 함수
2. parseInt, parseFloat 함수 (문자열만 숫자 타입으로 변환 가능)
3. \+ 단항 연산자 사용
4. \* 산술 연산자 사용

#### \_\_9.3.3 불리언 타입으로 변환

1. Boolean 생성자 함수
2. ! 부정 논리 연산자 두 번 사용

```javascript
!!"x"; // true
!!NaN; // false
!!Infinity; // true
```

<hr>

### 9.4 단축 평가

**단축 평가**: 표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평과 과정을 생략하는 것

#### \_\_9.4.1 논리 연산자를 사용한 단축 평가

```javascript
"Cat" || "Dog"; // "Cat"
"Cat" || false; // "Cat"
```

```javascript
var done1 = true;
var message1 = "";
message1 = done1 && "완료"; // "완료" 할당

var done2 = false;
var message2 = "";
message2 = done2 && "미완료"; // "미완료" 할당
```

- 단축 평가가 유용하게 사용되는 상황

  1. 객체를 가리키기 기대하는 변수가 null/undefined가 아닌지 확인하고 프로퍼티 참조

  ```javascript
  var elem = null;
  var value = elem && elem.value;
  ```

  2. 함수 매개변수에 기본값을 설정할 때

  ```javascript
  function getStringLength(str = "") {
    return str.length;
  }
  ```

#### \_\_9.4.2 옵셔널 체이닝 연산자

- ?.: 좌항의 피연산자가 null 또는 undefined인 경우 undefined 반환, 그렇지 않으면 우항의 프로퍼티 참조

```javascript
var elem = null;
var value = elem?.value; // undefined
```

- 논리 연산자 && ➡️ 좌항 피연산자가 Falsy 값이면 좌항 피연산자를 그대로 반환

  좌항 피연산자가 Falsy 값인 0이나 ''인 경우도 마찬가지

#### \_\_9.4.3 null 병합 연산자

- ??: 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자 반환, 그렇지 않으면 좌항의 피연산자 반환

  기본값 설정할 때 유용

```javascript
var foo = null ?? "default string"; // "default string"
```
