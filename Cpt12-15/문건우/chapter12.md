# 제 12장. 함수

---

## 함수

- 프로그래밍 언어의 함수는 일련의 과정을 문(statement)으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의한 것.

```javascript
function add(x, y) {
  // add = 함수 이름 / x, y = 매개변수
  return x + y; // 반환값
}
add(2, 5); // 2, 5 = 인수 / 함수 호출

var result = add(2, 5); // 7

console.log(result); // 7
```

### 함수는 왜 사용할까?

- 코드의 재사용이라는 측면에서 매우 유용.
- 함수는 코드의 가독성을 높이고 유지보수를 쉽게 해준다.

### 함수 리터럴

- 함수는 객체 타입의 값이다.
- 함수 리터럴은 function 키워드, 함수 이름, 매개변수 목록, 함수 몸체로 구성된다.

```javascript
// 함수 리터럴
var f = function add(x, y) {
  return x + y;
};
```

- 함수는 일반 객체와는 다르다. 함수는 호출할 수 있지만 일반 객체는 호출할 수 없다.

---

### 함수 정의

- 함수를 정의하는 방법은 4가지가 있다.

  1. 함수 선언문
  2. 함수 표현식
  3. Function 생성자 함수
  4. 화살표 함수

  ```javascript
  // 1. 함수 선언문
  function add(x, y) {
    return x + y;
  }

  // 2. 함수 표현식
  var add = function (x, y) {
    return x + y;
  };

  // 3. Function 생성자 함수
  var add = new Function("x", "y", "return x + y");

  // 4. 화살표 함수
  var add = (x, y) => x + y;
  ```

---

### 함수 생성 시점과 함수 호이스팅

- 함수 선언문 방식으로 정의한 함수의 경우 함수 호이스팅이 발생한다.
- 함수 표현식 방식으로 정의한 함수의 경우 함수 호이스팅이 발생하지 않는다.

```javascript
// 함수 선언문
console.log(add(2, 5)); // 7

function add(x, y) {
  return x + y;
}

// 함수 표현식
var add = function (x, y) {
  return x + y;
};

console.log(add(2, 5)); // 7
```

- 함수 표현식으로 함수를 정의하면 함수 호이스팅이 발생하는 것이 아니라 변수 호이스팅이 발생한다.

---

### 함수 호출

![함수 호출 과정](https://velog.velcdn.com/images/gyeongmi_lee/post/53b8bc71-e43f-4ec6-9bc2-16d8130de62d/image.png)

- 함수를 호출하면 함수 몸체의 문들이 실행되고, 실행 결과가 반환된다.
- 함수를 호출할 때 인수를 전달하면 매개변수에 인수가 바인딩된다.
- 함수는 매개변수의 개수와 인수의 개수가 일치하는지 확인하지 않는다.

---

## 다양한 함수의 형태

### 즉시 실행 함수

- 함수를 정의함과 동시에 즉시 실행되는 함수.
- 함수를 정의하자마자 즉시 실행하고 싶을 때 사용한다.

```javascript
(function () {
  var a = 3;
  var b = 5;
  return a * b;
})();
```

### 재귀 함수

- 함수가 자기 자신을 호출하는 것.
- 재귀 함수는 반드시 종료 조건을 만들어야 한다.

```javascript
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}
```

### 중첩 함수

- 함수 내부에 함수를 정의하는 것.
- 중첩 함수는 자신을 둘러싼 외부 함수의 변수에 접근할 수 있다.

```javascript
function outer() {
  var x = 1;

  function inner() {
    var y = 2;
    console.log(x + y);
  }

  inner();
}

outer(); // 3
```

### 콜백 함수

- 함수의 매개변수를 통해 다른 함수의 내부로 전달되는 함수
- 매개변수를 통해 함수의 외부에서 함수를 전달받은 함수를 고차 함수라고 한다.

```javascript
function repeat(n, f) {
  for (var i = 0; i < n; i++) {
    f(i);
  }
}

var logAll = function (i) {
  console.log(i);
};

repeat(5, logAll);
```

### 순수 함수와 비순수 함수

- 순수 함수: 동일한 인수로 호출된 함수는 언제나 동일한 결과를 반환하고 외부 상태에 부수 효과(side effect)가 없는 함수.
- 비순수 함수: 순수 함수가 아닌 함수.

---
