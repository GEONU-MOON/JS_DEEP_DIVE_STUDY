# 17장. 생성자 함수에 의한 객체 생성

---

## 17.1 Object 생성자 함수

- Object 생성자 함수를 new 연산자와 함께 호출하여 객체를 생성한다. 이때 생성된 객체를 Object 생성자 함수가 생성한 객체라고 부른다.
- Object 생성자 함수는 전역 객체의 메서드다. 따라서 Object 생성자 함수를 호출하여 객체를 생성하면 전역 객체의 메서드를 상속받는 객체가 된다.

```javascript
const person = new Object();
person.name = "Lee";
person.sayHello = function () {
  console.log("Hi! My name is " + this.name);
};

console.log(person); // { name: 'Lee', sayHello: [Function: sayHello] }
person.sayHello(); // Hi! My name is Lee
```

- Object 생성자 함수를 통해 객체를 생성하는 방식은 일반적이지 않다. 대부분의 객체는 객체 리터럴 방식이나 생성자 함수 방식으로 생성한다.

## 17.2 생성자 함수

- 생성자 함수(constructor function)는 객체를 생성하는 함수다. 생성자 함수에 의해 생성된 객체를 인스턴스(instance)라고 한다.
- 생성자 함수는 일반 함수와 동일하게 함수 선언문, 함수 표현식, 클래스로 정의할 수 있다.

```javascript
// 생성자 함수
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

// 인스턴스 생성
const circle1 = new Circle(5);
const circle2 = new Circle(10);

console.log(circle1.getDiameter()); // 10
console.log(circle2.getDiameter()); // 20
```

- 생성자 함수의 역할은 프로퍼티 구조가 동일한 인스턴스를 생성하는 것이다. 따라서 생성자 함수를 통해 생성된 인스턴스는 프로퍼티 구조가 동일하다.

## 17.3 생성자 함수의 인스턴스 생성 과정

- 생성자 함수를 호출하면 다음과 같은 과정을 거쳐 인스턴스가 생성된다.

  1. 인스턴스 생성과 this 바인딩
  2. 인스턴스 초기화
  3. 인스턴스 반환

  ### 17.3.1 인스턴스 생성과 this 바인딩

  - 생성자 함수가 호출되면 함수 몸체의 가장 앞에서 빈 객체를 생성한다. 이때 생성된 빈 객체는 this에 바인딩된다.
  - 생성자 함수 몸체의 코드는 암묵적으로 this에 바인딩되어 있는 빈 객체를 가리킨다.

  ### 17.3.2 인스턴스 초기화

  - this에 바인딩되어 있는 빈 객체에 프로퍼티 또는 메서드를 추가하여 초기화한다.

  ### 17.3.3 인스턴스 반환

  - 생성자 함수 내부에서 명시적으로 this가 아닌 다른 객체를 반환하면 this가 반환되지 않는다.
  - 생성자 함수 내부에서 명시적으로 객체를 반환하지 않으면 this가 암묵적으로 반환된다.

## 17.4 내부 메서드 [[Call]]과 [[Construct]]

- 함수 객체는 일반 객체와 달리 호출할 수 있다. 함수 객체는 [[Call]]이라는 내부 메서드를 갖고 있다.

## 17.5 constructor와 non-constructor의 구분

- constructor와 non-constructor를 구분하는 기준은 new 연산자다. new 연산자와 함께 생성자 함수로 호출하면 constructor로 동작하고, 그렇지 않으면 non-constructor로 동작한다.

## 17.6 new 연산자

- new 연산자와 함께 생성자 함수를 호출하면 해당 함수는 생성자 함수로 동작한다. 생성자 함수가 생성한 인스턴스를 반환한다.

### 17.6.1 new.target

- new.target은 함수 내부에서 함수 자신이 new 연산자와 함께 호출되는지 확인하기 위해 사용한다.

```javascript
function Circle(radius) {
  if (!new.target) {
    return new Circle(radius);
  }
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

const circle = Circle(5);
console.log(circle.getDiameter()); // 10
```
