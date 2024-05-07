# 제 9장. 타입 변환과 단축 평가

---

### 타입 변환이란?

- 자바스크립트의 모든 값은 타입이 있다.
- 타입 변환이란 해당 값의 타입을 다른 타입으로 변환하는 것을 의미한다.
- 타입 변환은 명시적 타입 변환(타입 캐스팅)과 암묵적 타입 변환(타입 강제 변환)으로 구분할 수 있다.

```javascript
// 명시적 타입 변환
var x = 10;
var str = x.toString();
console.log(typeof str, str); // string 10

// 암묵적 타입 변환
var x = 10;
var str = x + '';
console.log(typeof, x, x); // number 10
console.log(typeof str, str); // string 10
```

---

### 암묵적 타입 변환

- 자바스크립트 엔진은 표현식을 평가할 때 개발자가 의도하지 않았지만 코드 실행을 위해 필요한 타입으로 암묵적 타입 변환을 실행한다.

#### 문자열 타입으로 변환

- 문자열 연결 연산자는 피연산자 중 하나 이상이 문자열이 아닌 경우 문자열로 타입을 변환한다.

```javascript
true + ""; // 'true'
10 + ""; // '10'
```

#### 숫자 타입으로 변환

- 산술 연산자는 피연산자 중 하나 이상이 숫자 타입이 아닌 경우 숫자 타입으로 타입을 변환한다.

```javascript
"10" - 5; // 5
"10" * 2; // 20
1 / "one"; // NaN(숫자 타입으로 변환할 수 없는 경우 NaN을 반환한다.)
```

#### 불리언 타입

- 자바스크립트 엔진은 불리언 타입으로의 타입 변환을 위해 Truthy와 Falsy 값을 구분한다.
- 자바스크립트 엔진은 Truthy(참으로 평가되는 값) 값을 true로, Falsy 값(거짓으로 평가되는 값)을 false로 강제 변환한다.

---

### 명시적 타입 변환

- 명시적 타입 변환은 개발자가 의도적으로 값의 타입을 변환하는 것을 의미한다.

#### 문자열 타입으로 변환

- String 생성자 함수를 new 연산자 없이 호출하는 방법과 Object.prototype.toString 메서드를 사용하는 방법이 있다.

```javascript
// String 생성자 함수를 new 연산자 없이 호출하는 방법
String(1); // '1'
String(NaN); // 'NaN'
String(true); // 'true'

// Object.prototype.toString 메서드를 사용하는 방법
(1).toString(); // '1'
NaN.toString(); // 'NaN'
true.toString(); // 'true'
```

#### 숫자 타입으로 변환

- Number 생성자 함수를 new 연산자 없이 호출하는 방법과 parseInt, parseFloat 함수를 사용하는 방법이 있다.

```javascript
// Number 생성자 함수를 new 연산자 없이 호출하는 방법
Number("0"); // 0
Number("-1"); // -1
Number("10.53"); // 10.53

// parseInt, parseFloat 함수를 사용하는 방법
parseInt("0"); // 0
parseInt("-1"); // -1
parseInt("10.53"); // 10
parseFloat("10.53"); // 10.53
```

#### 불리언 타입으로 변환

- Boolean 생성자 함수를 new 연산자 없이 호출하는 방법과 ! 연산자를 두 번 사용하는 방법이 있다.

```javascript
// Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
Boolean("x"); // true
Boolean(""); // false
Boolean(0); // false

// ! 연산자를 두 번 사용하는 방법
!!"x"; // true
!!""; // false
!!0; // false
```

---

### 단축 평가

#### 논리 연산자를 사용한 단축 평가

- 논리 연산자는 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다.
- 논리합(||) 연산자는 둘 중 하나만 true로 평가되어도 true를 반환하고, 논리곱(&&) 연산자는 둘 다 true로 평가되어야 true를 반환한다.

```javascript
"Cat" || "Dog"; // 'Cat'
false || "Dog"; // 'Dog'
"Cat" && "Dog"; // 'Dog'
false && "Dog"; // false
```

- 단축 평가는 표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평가 과정을 생략하는 것을 의미한다.

#### 옵셔널 체이닝 연산자

- 옵셔널 체이닝 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

```javascript
var elem = null;

// elem이 null 또는 undefined이면 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.
var value = elem?.value;
console.log(value); // undefined
```

#### null 병합 연산자

- null 병합 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

```javascript
// 좌항의 피연산자가 null 또는 undefined이면 우항의 피연산자를 반환하고,
// 그렇지 않으면 좌항의 피연산자를 반환한다.
var foo = null ?? "default string";
console.log(foo); // 'default string'
```
