# 제 14장. 전역 변수의 문제점

---

## 변수의 생명 주기

### 지역 변수의 생명 주기

- 지역 변수는 함수가 호출될 때 생성되고 함수가 종료될 때 소멸된다.
- 지역 변수는 함수 내에서만 사용할 수 있으며 함수 외부에서는 사용할 수 없다.
- 지역 변수의 생명 주기는 함수의 호출과 종료에 의해 결정된다.

### 전역 변수의 생명 주기

- 전역 변수는 프로그램이 시작될 때 생성되고 프로그램이 종료될 때 소멸된다.
- 전역 변수는 프로그램 전체에서 사용할 수 있으며 모든 함수에서 접근할 수 있다.
- 전역 변수의 생명 주기는 프로그램의 시작과 종료에 의해 결정된다.

### 전역 변수의 사용을 억제하는 방법

- 전역 변수를 반드시 사용해야 하는 경우가 아니라면 지역 변수를 사용하는 것이 좋다.
- 변수의 스코프는 좁을수록 좋다.

#### 즉시 실행 함수

- 모든 코드를 즉시 실행 함수로 감싸면 모든 변수는 즉시 실행 함수의 지역 변수가 된다.

```javascript
(function () {
  var foo = 10; // 즉시 실행 함수의 지역 변수
  // ...
})();

console.log(foo); // ReferenceError: foo is not defined
```

#### 네임스페이스 객체

- 전역에 네임스페이스 역할을 담당할 전역 객체를 생성하고 전역 변수처럼 사용하고 싶은 변수를 프로퍼티로 추가하는 방법이다.
  - 네임스페이스란? -> 네임스페이스는 프로그래밍에서 변수, 함수 등의 식별자들이 충돌하지 않도록 관리하는 방법으로, 각각의 식별자를 그룹화하여 유일한 영역을 만드는 개념

```javascript
// 네임스페이스 객체 생성
var myNamespace = {};

// 전역 변수처럼 사용하고 싶은 변수를 프로퍼티로 추가
myNamespace.globalVariable = 10;

// 함수도 추가할 수 있습니다.
myNamespace.myFunction = function () {
  console.log("This is a function within myNamespace");
};

// 사용 예시
console.log(myNamespace.globalVariable); // 10
myNamespace.myFunction(); // This is a function within myNamespace
```

#### 모듈 패턴

- 모듈 패턴은 전역 변수를 억제하고 모듈 내에서 공개 및 비공개 데이터를 관리할 수 있는 방법이다.

```javascript
var Counter = (function () {
  // private 변수
  var num = 0;

  // 외부로 공개할 데이터나 메서드를 프로퍼티로 추가한 객체를 반환한다.
  return {
    increase() {
      return ++num;
    },
    decrease() {
      return num > 0 ? --num : 0;
    },
  };
})();
```
