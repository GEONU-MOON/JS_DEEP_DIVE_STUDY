


- this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수이다.
- this를 사용하는 이유는 인스턴스 변수와 지역 변수의 이름이 같을 때 인스턴스 변수임을 명확히 하기 위해서이다.

### this 바인딩? 
- this가 가리키는 대상이 무엇인지 결정하는 것을 의미한다. 
- this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.

### 22.2 함수 호출 방식과 this 바인딩

- 함수를 호출하는 방식은 다음과 같다.
  1. 일반 함수 호출
  2. 메서드 호출
  3. 생성자 함수 호출
  4. Function.prototype.apply/call/bind 메서드에 의한 간접 호출

```js
function foo() {
  console.dir(this);
}
```


### `call`

- call 메서드는 모든 함수에서 사용할 수 있으며, this를 특정 값으로 지정하여 함수를 호출할 수 있다.
- call 메서드의 첫 번째 인수로는 this에 바인딩할 값(객체)를 전달한다.
- **용도**: 함수 호출 시 `this`를 명시적으로 설정하고, 인자를 개별적으로 전달합니다.
- **구문**
  ```javascript
  func.call(thisArg, arg1, arg2, ...);
  ```
- **예제**
  ```javascript
  function greet(greeting) {
    console.log(greeting + ", " + this.name);
  }

  const person = { name: "John" };
  greet.call(person, "Hello"); // 출력: Hello, John
  ```

### `apply`

- **용도** 함수 호출 시 `this`를 명시적으로 설정하고, 인자를 배열 형태로 전달합니다.
- **구문**
  ```javascript
  func.apply(thisArg, [arg1, arg2, ...]);
  ```
- **예제**
  ```javascript
  function greet(greeting) {
    console.log(greeting + ", " + this.name);
  }

  const person = { name: "John" };
  greet.apply(person, ["Hello"]); // 출력: Hello, John
  ```

### `bind`

- **용도** `this` 값과 초기 인자들을 영구적으로 설정한 새로운 함수를 반환합니다.
- **구문**
  ```javascript
  const boundFunc = func.bind(thisArg, arg1, arg2, ...);
  ```
- **예제**
  ```javascript
  function greet(greeting) {
    console.log(greeting + ", " + this.name);
  }

  const person = { name: "John" };
  const greetPerson = greet.bind(person, "Hello");
  greetPerson("!"); // 출력: Hello, John!
  ```

### 요약

- `call`과 `apply`는 즉시 함수를 호출하며, `this`와 인자를 설정합니다.  - 둘의 차이는 그냥 인자를 각각 전달하느냐, 배열로 전달하느냐의 차이뿐
- `bind`는 새로운 함수를 반환하며, 이 함수는 나중에 호출될 때 `this`와 초기 인자들이 고정됩니다.


### 22.3 함수 호출 방식과 this 바인딩 정리

| 함수 호출 방식 | this 바인딩 |
| --- | --- |
| 일반 함수로서 호출 | 전역 객체 |
| 메서드로서 호출 | 메서드를 호출한 객체 |
| 생성자 함수로서 호출 | 생성자 함수가 (미래에) 생성할 인스턴스 |
| Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 인수로 전달한 객체 |
