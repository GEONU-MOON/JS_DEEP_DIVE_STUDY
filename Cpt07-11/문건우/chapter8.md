# 제 8장. 제어문

---

## 블록문

- 블록문은 0개 이상의 문을 중괄호로 묶은 것으로 코드 블록 또는 블록이라고 부른다.
- 자바스크립트는 블록문을 하나의 단위로 취급한다.
- 자체 종결성을 갖기 때문에 세미콜론으로 끝내지 않는다.

```javascript
// 블록문
{
  var foo = 10;
}

// 제어문
var x = 1;
if (x < 10) {
  x++;
}

// 함수 선언문
function sum(a, b) {
  return a + b;
}
```

---

### 조건문

- 조건문은 주어진 조건식의 평가 결과에 따라 코드 블록을 실행한다.
- 자바스크립트는 if, else if, else 문을 사용하여 조건문을 표현한다.

#### if ... else 문

```javascript
var num = 2;
var kind;

if (num > 0) {
  kind = "양수";
} else if (num < 0) {
  kind = "음수";
} else {
  kind = "영";
}

console.log(kind); // 양수
```

#### switch 문

- switch 문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮긴다.
- case 문의 값과 일치하는 값이 없다면 default 문으로 실행 흐름을 옮긴다.

```javascript
var month = 4;
var monthName;

switch (month) {
case 1:
    monthName = 'January';
    break;
case 2:
    monthName = 'February';
    break;
case 3:
    monthName = 'March';
    break;
case 4:
    monthName = 'April';
    break;

console.log(monthName); // April
```

---

### 반복문

- 반복문은 조건식의 평가 결과가 참인 경우 코드 블록을 실행한다.
- 자바스크립트는 for, while, do ... while 문을 사용하여 반복문을 표현한다.

#### for 문

- for 문은 세미콜론으로 구분된 세 개의 옵션으로 구성된다.
- for (변수 선언문 또는 할당문; 조건식; 증감식) { ... }

```javascript
for (var i = 0; i < 2; i++) {
  console.log(i);
}
// 0
// 1
```

#### while 문

- while 문은 주어진 조건식의 평가 결과가 참이면 코드 블록을 실행한다.

```javascript
var count = 0;

while (count < 3) {
  console.log(count);
  count++;
}
// 0
// 1
// 2
```

#### do while 문

- do while 문은 코드 블록을 먼저 실행하고 조건식을 평가한다.

```javascript
var count = 0;

do {
  console.log(count);
  count++;
} while (count < 3);
// 0
// 1
// 2
```

---

### break 문

- break 문은 코드 블록을 탈출한다.
- 레이블 문, 반복문, switch 문의 코드 블록을 탈출한다.

```javascript
for (var i = 0; i < 3; i++) {
  console.log(i);
  if (i === 1) break;
}
// 0
// 1
```

---

### continue 문

- continue 문은 코드 블록 실행을 중단하고 반복문의 증감식으로 실행 흐름을 이동한다.

```javascript
for (var i = 0; i < 3; i++) {
  if (i === 1) continue;
  console.log(i);
}
// 0
// 2
```

---
