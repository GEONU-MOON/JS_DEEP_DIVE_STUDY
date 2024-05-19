### [[Call]]

- `[[Call]]` 내부 메서드는 함수를 호출할 때 실행됩니다. 
- 함수 호출 시 `[[Call]]` 메서드가 실행되어 함수의 본문이 실행됩니다. 
- 이때 `this` 바인딩과 인수 전달 등의 작업이 이루어집니다.

```javascript
function foo() {
  console.log('foo was called');
}

foo(); // 'foo was called'
```
- `foo()`가 호출될 때, `foo` 함수의 `[[Call]]` 메서드가 실행됩니다. 
- `[[Call]]` 메서드는 함수의 본문을 실행하고, 필요한 경우 `this`를 설정합니다.

### [[Construct]]

- `[[Construct]]` 내부 메서드는 함수를 생성자로 호출할 때 실행됩니다.
- `new` 키워드를 사용하여 함수를 호출하면 `[[Construct]]` 메서드가 실행되고, 새로운 객체가 생성됩니다.

```javascript
function Bar() {
  this.message = 'Bar was constructed';
}

const barInstance = new Bar();
console.log(barInstance.message); // 'Bar was constructed'
```

위 코드에서 `new Bar()`가 호출될 때, `Bar` 함수의 `[[Construct]]` 메서드가 실행됩니다. `[[Construct]]` 메서드는 다음과 같은 작업을 수행합니다:

1. 새로운 객체를 생성합니다.
2. 생성된 객체의 `[[Prototype]]`을 설정합니다.
3. 생성된 객체를 `this`로 바인딩하여 함수 본문을 실행합니다.
4. 객체를 반환합니다.

### 함수의 [[Call]]과 [[Construct]] 차이점

- **[[Call]]**: 함수가 일반적으로 호출될 때 실행됩니다. 함수가 호출되어 함수 본문이 실행되고, 반환 값이 있을 경우 반환합니다.
- **[[Construct]]**: 함수가 생성자로 호출될 때 실행됩니다. `new` 키워드를 사용하여 호출되면 새로운 객체를 생성하고, 해당 객체를 반환합니다.

### 활용 예시

```javascript
function Example() {
  if (new.target) {
    // [[Construct]] 메서드가 호출됨
    this.message = 'Example instance created';
  } else {
    // [[Call]] 메서드가 호출됨
    console.log('Example function called');
  }
}

Example(); // 'Example function called'

const exampleInstance = new Example();
console.log(exampleInstance.message); // 'Example instance created'
```

- `new.target`을 사용하여 함수가 생성자로 호출되었는지 확인가능.
- 생성자로 호출되면 새로운 객체를 생성하고 아니면 일반 함수로서 동작한다.

### 요약

- `[[Call]]`은 함수가 일반적으로 호출될 때 실행되며, 함수의 본문을 실행
- `[[Construct]]`은 함수가 생성자로 호출될 때 실행되며, 새로운 객체를 생성하고 초기화
- `new.target`을 사용하면 함수가 생성자로 호출되었는지 확인할 수 있다.
