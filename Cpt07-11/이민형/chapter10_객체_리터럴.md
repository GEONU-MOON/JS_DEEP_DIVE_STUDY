## 10장 객체 리터럴

### 10.1 객체란?

_자바스크립트를 구성하는 거의 "모든 것"이 객체다._

- 원시값을 제외한 나머지 값(함수, 배열, 정규 표현식 등)은 모두 객체

**원가 값은 변경 붕가능한 값이지만 객체는 변경 가능한 값이다.**

- 함수도 프로퍼티 값으로 사용 가능 ➡️ 프로퍼티 값 함수는 일반 함수와 구분하기 위해 메서드라고 부른다.

```javascript
var counter = {
  num: 0, // 프로퍼티
  increase: function () {
    this.num++;
  }, // 메서드
};
```

- 프로퍼티: 객체의 상태를 나타내는 값(data)
- 메서드: 프로퍼티(상태 데이터)를 참조하고 조작할 수 있는 동작

<hr>

### 10.2 객체 리터럴에 의한 객체 생성

_객체 리터럴의 중괄호는 코드 블록을 의미하지 않는다는 데 주의하자._

- 객체 생성 방법
  - 객체 리터럴
  - Object 생성자 함수
  - 생성자 함수
  - Object.create 메서드
  - 클래스(ES6)

<hr>

#### 10.3 프로퍼티

객페는 프로퍼티의 집합
프로퍼티는 키와 값으로 구성

<hr>

### 10.4 메서드

메서드는 객체에 묶여있는 함수를 의미

<hr>

### 10.5 프로퍼티 접근

- 프로퍼티 접근 방법

  - 마침표 표기법

    마침표 접근 연산자(.) 사용

  - 대괄호 표기법

    대괄호 접근 연산자([...]) 사용

```javascript
var person = {
  name: "Lee",
};

// 마침표 표기법으로 접근
console.log(person.name);
// 대괄호 표기법으로 접근
console.log(person["name"]);
```

**객체에 존재하지 않는 프로퍼티에 접근하면 ReferenceError가 아닌 undefined을 반환한다.**

- ex

```javascript
var person = {
  "last-name": "Lee",
  1: 10,
};

person.last - name;
// 브라우저: NaN
// Node.js: ReferenceError: name is not defined
```

> 브라우저 환경: person.last가 없어서 undefined ➡️ undefined에 name이라는 식별자를 찾아 - 연산을 하려고 함. ➡️ 브라우저 환경에서는 name이라는 전역 변수가 암묵적으로 존재 ➡️ 결과 NaN
