# 제 10장. 객체 리터럴

---

## 객체란?

- 자바스크립트는 객체 기반의 프로그래밍 언어이며, 자바스크립트를 이루고 있는 거의 모든 것이 객체이다.
- 원시 값(문자열, 숫자, 불리언, null, undefined, 심벌)을 제외한 나머지 값(객체, 함수, 배열 등)은 모두 객체이다.
- 원시 타입의 값은 변경 불가능한 값이지만 객체 타입의 값은 변경 가능한 값이다.
- 객체는 0개 이상의 프로퍼티로 구성된 집합이며, 프로퍼티는 키(key)와 값(value)으로 구성된다.
  ![객체](https://velog.velcdn.com/images%2Fseeh_h%2Fpost%2F5808a553-e869-4a38-8d1a-ec921f028085%2Fimage.png)
  - 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메서드라 부른다.
  - 프로퍼티 : 객체의 상태를 나타내는 값
  - 메서드 : 프로퍼티를 참조하거나 조작할 수 있는 동작
  - 객체는 데이터(프로퍼티)와 동작(메서드)을 모두 포함할 수 있기 때문에 데이터와 동작을 하나의 단위로 구조화할 수 있어 유용하다.

---

### 객체 리터럴에 의한 객체 생성

- 자바스크립트는 객체 리터럴에 의해 객체를 생성하는 간편한 문법을 제공한다.
  - 객체 리터럴
  - Object 생성자 함수
  - 생성자 함수
  - Object.create 메서드
  - 클래스(ES6)
- 객체 리터럴은 중괄호({})로 표현하며, 중괄호 내에 0개 이상의 프로퍼티를 정의하고 변수에 할당되는 시점에 자바스크립트 엔진은 객체 리터럴을 해석해 객체를 생성한다.
- 만약 중괄호 내에 프로퍼티를 정의하지 않으면 빈 객체가 생성된다.

```javascript
// 빈 객체 생성
var person = {};

// 프로퍼티 추가
person.name = "Lee";
person.sayHello = function () {
  console.log("Hi! My name is " + this.name);
};

console.log(typeof person); // object
console.log(person); // { name: 'Lee', sayHello: [Function (anonymous)] }
person.sayHello(); // Hi! My name is Lee
```

---

### 프로퍼티

- 객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성된다.
- 프로퍼티 키 : 프로퍼티를 식별하기 위한 식별자
- 프로퍼티 값 : 프로퍼티 키를 통해 접근할 수 있는 값
- 프로퍼티 키는 빈 문자열을 포함하는 모든 문자열 또는 심벌 값이 사용될 수 있으며, 프로퍼티 값은 모든 값이 사용될 수 있다.

```javascript
var person = {
  name: "Lee",
  age: 20,
};

console.log(person); // { name: 'Lee', age: 20 }
```

- 프로퍼티 키에는 문자열 뿐만 아니라 숫자도 사용할 수 있다.

---

### 메서드

- 객체에 포함된 함수를 메서드라고 부른다.
- 메서드는 객체에 제한되어 있는 함수를 의미하며, 객체에 포함된 함수를 메서드라고 부른다.

```javascript
var circle = {
  radius: 5, // ← 프로퍼티
  getDiameter: function () {
    // ← 메서드
    return 2 * this.radius;
  },
};

console.log(circle.getDiameter()); // 10
```

- 메서드 내부에서 this 키워드를 사용하면 객체에 바인딩된다.

---

### 프로퍼티 접근

- 프로퍼티에 접근하는 방법은 두 가지가 있다.
  - 마침표 프로퍼티 접근 연산자(.) : 객체.프로퍼티
  - 대괄호 프로퍼티 접근 연산자([]) : 객체['프로퍼티']

```javascript
var person = {
  name: "Lee",
};

// 마침표 프로퍼티 접근 연산자
console.log(person.name); // Lee
// 대괄호 프로퍼티 접근 연산자
console.log(person["name"]); // Lee
```

- 객체에 존재하지 않는 프로퍼티에 접근하면 undefined가 반환된다.

---

### 프로퍼티 값 갱신

- 이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신된다.

```javascript
var person = {
  name: "Lee",
};

console.log(person.name); // Lee

// 프로퍼티 값 갱신
person.name = "Kim";

console.log(person.name); // Kim
```

---

### 프로퍼티 동적 생성

- 객체는 동적으로 프로퍼티를 생성할 수 있다.

```javascript
var person = {
  name: "Lee",
};

// person 객체에 age 프로퍼티가 존재하지 않으므로 동적으로 생성되고 값이 할당된다.
person.age = 20;

console.log(person); // { name: 'Lee', age: 20 }
```

---

### 프로퍼티 삭제

- delete 연산자를 사용하면 객체의 프로퍼티를 삭제할 수 있다.

```javascript
var person = {
  name: "Lee",
};

// 프로퍼티 삭제
delete person.name;

console.log(person); // {}
```

---

### ES6에서 추가된 객체 리터럴의 확장 기능

#### 프로퍼티 축약 표현

- ES6에서는 객체 리터럴의 기능이 확장되어 객체 리터럴 내부에서도 계산된 프로퍼티 이름과 메서드 축약 표현을 사용할 수 있다.

```javascript
// ES6에서 추가된 객체 리터럴의 확장 기능
var x = 1,
  y = 2;

// ES6의 계산된 프로퍼티 이름
var obj = {
  x,
  y,
};

console.log(obj); // { x: 1, y: 2 }

// ES6의 메서드 축약 표현
var obj = {
  name: "Lee",
  sayHi() {
    console.log("Hi! " + this.name);
  },
};

obj.sayHi(); // Hi! Lee
```

#### 계산된 프로퍼티 이름

- ES6에서는 객체 리터럴 내부에서도 계산된 프로퍼티 이름을 사용할 수 있다.

```javascript
// ES6의 계산된 프로퍼티 이름
var prefix = "prop";
var i = 0;

var obj = {
  [prefix + ++i]: i,
  [prefix + ++i]: i,
  [prefix + ++i]: i,
};

console.log(obj); // { prop1: 1, prop2: 2, prop3: 3 }
```

#### 메서드 축약 표현

- ES6에서는 객체 리터럴 내부에서도 메서드 축약 표현을 사용할 수 있다.

```javascript
// ES6의 메서드 축약 표현
var obj = {
  name: "Lee",
  sayHi() {
    console.log("Hi! " + this.name);
  },
};

obj.sayHi(); // Hi! Lee
```

---
