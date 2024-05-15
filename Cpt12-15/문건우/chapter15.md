# 제 15장. let, const 키워드와 블록 레벨 스코프

---

## var 키워드로 선언한 변수의 문제점

#### 1. 변수 중복 선언 허용

- var 키워드로 선언한 변수는 중복 선언이 허용된다.

```javascript
var x = 1;
var y = 2;

// var 키워드로 선언한 변수는 중복 선언이 허용된다.
var x = 100;
// 초기화문이 없는 변수 선언은 무시된다.
var y;
```

#### 함수 레벨 스코프

- var 키워드로 선언한 변수는 오로지 함수의 코드 블록만을 지역 스코프로 인정한다.

```javascript
var x = 1;

if (true) {
  // var 키워드로 선언한 변수는 함수 레벨 스코프를 갖는다.
  // 함수 밖에서 선언한 변수와 같은 이름의 변수를 중복 선언한다.
  var x = 10;
}

console.log(x); // 10
```

### 변수 호이스팅

- var 키워드로 선언한 변수는 변수 호이스팅이 발생한다.

```javascript
// 이 시점에는 변수 호이스팅에 의해 이미 foo 변수가 선언되었다(1. 선언 단계).
// 변수 foo는 undefined로 초기화된다(2. 초기화 단계).
console.log(foo); // undefined

// 변수에 값을 할당(3. 할당 단계).
foo = 123;

console.log(foo); // 123

// 변수 선언은 런타임 이전에 자바스크립트 엔진에 의해 암묵적으로 실행된다.
var foo;
```

---

## let 키워드

- var의 단점을 보완하기 위해 let 키워드가 도입되었다.

#### 1. 변수 중복 선언 금지

- let 키워드로 선언한 변수는 중복 선언이 금지된다.

```javascript
let x = 1;

// let 키워드로 선언한 변수는 중복 선언이 금지된다.
let x = 100; // SyntaxError: Identifier 'x' has already been declared
```

#### 2. 블록 레벨 스코프

- let 키워드로 선언한 변수는 블록 레벨 스코프를 갖는다.
- 블록 레벨 스코프란 코드 블록이 지역 스코프를 만든다는 것을 의미한다.

```javascript
let foo = 1; // 전역 변수

{
  let foo = 2; // 지역 변수
  let bar = 3; // 지역 변수
}

console.log(foo); // 1
console.log(bar); // ReferenceError: bar is not defined
```

#### 3. 변수 호이스팅

- let 키워드로 선언한 변수는 변수 호이스팅이 발생하지만 var 키워드로 선언한 변수와 달리 일시적 사각지대(Temporal Dead Zone; TDZ)에 빠진다.

```javascript
// var 키워드로 선언한 변수는 런타임 이전에 선언 단계와 초기화 단계가 실행된다.
// 따라서 변수 선언문 이전에 변수를 참조할 수 있다.
console.log(foo); // undefined

var foo;
console.log(foo); // undefined

foo = 1; // 할당문에서 초기화된다.
console.log(foo); // 1
```

---

## const 키워드

- const 키워드는 상수를 선언하기 위해 사용한다.

#### 1. 선언과 초기화

- const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.

```javascript
const foo = 1;
console.log(foo); // 1
```

#### 2. 재할당 금지

- const 키워드로 선언한 변수는 재할당이 금지된다.

```javascript
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable.
```

#### 3. 상수

- const 키워드로 선언한 변수에 원시 값(상수)을 할당한 경우, 값을 변경할 수 없다.

```javascript
let preTaxPrice = 100;

// 세후 가격
// 0.1의 의미를 명확히 알기 어렵기 때문에 가독성이 좋지 않다.
let afterTaxPrice = preTaxPrice + preTaxPrice * 0.1;

console.log(afterTaxPrice); // 110
```

#### 4. const 키워드와 객체

- const 키워드로 선언한 변수에 객체를 할당한 경우, 값을 변경할 수 있다.

```javascript
const person = {
  name: "Lee",
};

// 객체는 변경 가능한 값이다.
// 따라서 프로퍼티를 추가, 삭제, 갱신할 수 있다.
person.name = "Kim";

console.log(person); // {name: "Kim"}
```

- const키워드는 재할당을 금지할 뿐이지 변경을 금지하지 않는다.

**_변수를 선언할 때는 일단 const키워드를 사용하자._**
