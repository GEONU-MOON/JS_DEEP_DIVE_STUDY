# 제 23장. 실행 컨텍스트

---

## 소스코드의 타입

- 소스코드를 4가지 타입으로 구분. 4가지 타입의 소스코드는 실행 컨텍스트를 생성하는데 영향을 미침
  1. 전역 코드
  2. 함수 코드
  3. eval 코드
  4. 모듈 코드

#### 1. 전역 코드 : 전역에 존재하는 소스코드

```javascript
let globalVariable = "I am a global variable"; // 전역 코드

console.log(globalVariable); // 전역 코드
function globalFunction() {
  // 함수 정의 자체는 전역 코드
  console.log("This is a global function"); // 함수 코드 (이 부분은 함수 내부에 있으므로 함수 코드)
}

globalFunction(); // 전역 코드
```

#### 2. 함수 코드 : 함수 내부에 존재하는 소스코드

```javascript
function outerFunction() {
  // 함수 코드
  let outerVariable = "I am an outer variable"; // 함수 코드

  function innerFunction() {
    // 함수 코드
    let innerVariable = "I am an inner variable"; // 함수 코드
  }

  innerFunction(); // 함수 코드
}

outerFunction(); // 전역 코드
```

#### 3. eval 코드 : eval 함수에 인수로 전달되어 실행되는 소스코드

```javascript
eval("let evalVariable = 'I am an eval variable';"); // eval 코드
console.log(evalVariable); // 전역 코드
```

#### 4. 모듈 코드 : 모듈 내부에 존재하는 소스코드

```javascript
// 모듈 코드
let moduleVariable = "I am a module variable"; // 모듈 코드

export default moduleVariable; // 모듈 코드
```

---

## 소스코드의 평가와 실행

- 자바스크립트 엔진은 소스코드를 두 단계에 걸쳐 처리
  1. 소스코드의 평가 : 변수, 함수, 클래스 등의 선언문만 실행하고, 실제 실행에 필요한 정보를 생성
  2. 소스코드의 실행 : 생성된 정보를 사용해 실제 실행을 수행

ex) 전역 코드의 평가와 실행

```javascript
var x = 1; // 전역 코드
x = 1;
```

1. 소스코드의 평가
   - 변수 선언문 var x; 먼저 실행. 이때 생성된 변수 식별자 x는 실행 컨텍스트가 관리하는 스코프에 등록하고 undefined로 초기화
2. 소스코드의 실행
   - 변수 할당문 x = 1; 실행. 이때 x에 1을 할당
   - 변수 x가 선언되어 있는지 확인. (실행 컨텍스트가 관리하는 스코프에 x가 등록되어 있는지 확인)

---

## 실행 컨텍스트의 역할

1. 전역 코드 평가 (Global Code Evaluation)

- 전역 코드 평가 과정에서는 전역 실행 컨텍스트(Global Execution Context)가 생성됨.
- 이 단계에서 전역 변수와 함수 선언이 메모리에 할당되고, 코드가 준비됨. (변수는 undefined로 초기화되고, 함수 선언은 함수 전체가 메모리에 로드.)

2. 전역 코드 실행 (Global Code Execution)

- 전역 코드 실행 단계에서는 생성된 전역 실행 컨텍스트가 활성화되고, 전역 코드가 실제로 실행.
- 이 단계에서 변수에 값이 할당되고, 함수 호출이 이루어짐.

3. 함수 코드 평가 (Function Code Evaluation)

- 함수 코드 평가 과정에서는 새로운 함수 실행 컨텍스트(Function Execution Context)가 생성.
- 이 단계에서 함수 내부의 변수와 함수 선언이 메모리에 할당.

4. 함수 코드 실행 (Function Code Execution)

- 함수 코드 실행 단계에서는 생성된 함수 실행 컨텍스트가 활성화되고, 함수 코드가 실제로 실행됨.
- 이 단계에서 함수 내부의 코드가 실행되면서 변수에 값이 할당되고, 다른 함수가 호출될 수 있음.

---

## 실행 컨텍스트 스택

- 실행 컨텍스트는 스택(Stack) 자료구조로 관리됨.
- 실행 컨텍스트 스택에는 실행 컨텍스트가 순차적으로 쌓이고, 실행이 종료되면 순차적으로 제거됨.
  - 전역 코드의 평가와 실행 : 전역 실행 컨텍스트가 생성되고, 실행 컨텍스트 스택에 푸시함
  - 함수 코드의 평가와 실행 : 함수 실행 컨텍스트가 생성되고, 실행 컨텍스트 스택에 푸시함
  - 함수 실행이 종료되면 실행 컨텍스트 스택에서 팝됨

---

## 렉시컬 환경

- 렉시컬 환경(Lexical Environment)은 실행 컨텍스트의 일부로서, 식별자와 그 식별자에 바인딩된 변수, 함수, 클래스 등의 정보를 관리.

---

## 실행 컨텍스트의 생성과 식별자 검색 과정

- 전역 객체 생성
- 전역 코드 평가
  1. 전역 실행 컨텍스트 생성
  2. 전역 렉시컬 환경 생성
     2-1. 전역 환경 레코드 생성
     2-1-1. 객체 환경 레코드 생성
     2-1-2. 선언적 환경 레코드 생성
     2-2. this 바인딩
     2-3. 외부 렉시컬 환경에 대한 참조 결정

---

## 실행 컨텍스트와 블록 레벨 스코프

- let, const 키워드로 선언한 변수는 블록 레벨 스코프를 갖음.
- var 키워드로 선언한 변수는 함수 레벨 스코프를 갖음.
