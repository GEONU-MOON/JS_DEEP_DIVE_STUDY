# 제 11장. 원시값과 객체 비교하기

---

### 원시값

- 원시 값은 불변값이다.
- 원시 값은 값 자체를 비교한다.
- 원시 값은 메모리 주소를 참조하지 않는다.
- 변수 값을 변경하기 위해 원시 값을 재할당하면 새로운 메모리 주소에 재할당한 값을 저장하고, 변수가 참조하는 메모리 주소가 변경된다.(불변성)
- 불변성을 갖는 원시 값을 할당한 변수는 재할당 이외에 변수 값을 변경할 수 있는 방법이 없다.

```javascript
var score = 80;
var copy = score;

console.log(score); // 80
console.log(copy); // 80

score = 100;

console.log(score); // 100
console.log(copy); // 80
```

---

### 객체

- 객체는 가변값이다.
- 객체는 참조값을 비교한다.
- 객체는 메모리 주소를 참조한다.
- 객체를 할당한 변수는 객체를 참조하고 있는 메모리 주소를 참조한다.
- 객체를 할당한 변수는 재할당 없이 객체를 변경할 수 있다.

```javascript
var person = {
  name: "Lee",
};

var copy = person;

console.log(person); // { name: 'Lee' }
console.log(copy); // { name: 'Lee' }

person.name = "Kim";

console.log(person); // { name: 'Kim' }
console.log(copy); // { name: 'Kim' }
```

---
