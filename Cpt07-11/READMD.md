# 2회차 섹션 공지

## 일시 및 장소
- **날짜**: 5월 7일 (화)

## 학습 분량
- **챕터**: 7장부터 11장까지

## 섹션 진행자
- **진행자**: 정종문

## 퀴즈 및 키워드 준비
- **퀴즈 출제자**: 섹션 진행자가 맡습니다.
- **키워드 제출**: 각자 학습한 챕터에서 중요하다고 생각하는 키워드 1개 이상.




------

### 2회차 섹션 퀴즈 정딥

### 1. Q : 각 줄마다 출력값을 작성해주세요

###### <span style="color:blue">1번 문제 실수 -> 기존에 아래 6번과 7번이 문자열0과 비교해야하는데, 오류가 있어서 수정했습니다. </span>

```js
let num = 5;
console.log(++num);  //  1번 -> 6 : 전위 증가 연산자로 num에 1을 더한 후 출력
console.log(num); //  2번 -> 1번에서 num에 1을 더했기 때문에 6이 출력
console.log(num++); //  3번 -> 후위 증가 연산자로 num을 출력한 후 1을 더함
console.log(num); //  4번  -> 3번에서 num에 1을 더했기 때문에 7이 출력
let str = '5';
console.log(++str + true); //  5번 -> 6 : 문자열 '5'에 전위 증가 연산자를 사용하여 6 + true는 1로 변환되어 7이 출력

##### 1번 문제 실수 -> 기존에 아래 6번과 7번이 문자열0과 비교해야하는데, 오류가 있어서 수정했습니다. 
console.log('0'===-0); // 6번  -> false : === 연산자는 값과 타입을 비교하기 때문에 false
console.log('0'==-0); // 7번 -> true : == 연산자는 타입을 변환하여 비교하기 때문에 true
console.log('0'==0); // 8번 -> true : == 연산자는 타입을 변환하여 비교하기 때문에 true
console.log(!null); // 9번 -> true : null은 falsy 값이기 때문에 true
console.log(!undefined); // 10번 -> true : undefined는 falsy 값이기 때문에 true
```

#### <span style="color:blue">FALSY 값이란 (조건문에서 false로 간주되는 값) </span>
>- false, 0, '', null, undefined, NaN, document.all

------

### 2. Q: 동등 비교 연산자와 비교 일치 연산자의 차이점을 설명하시오.

- 동등 비교 연산자(==) : 값만 비교하며, 타입은 비교하지 않는다.
- 일치 비교 연산자(===) : 값과 타입을 모두 비교한다.

### 2-1 Q: 그렇다면 다음 코드의 출력 결과를 예측하고, 이유를 설명하시오.
```js
console.log(5 == '5');  // true : 동등 비교 연산자는 타입을 변환하여 비교하기 때문에 true
console.log(5 === '5');  // false : 일치 비교 연산자는 값과 타입을 비교하기 때문에 false
```

##### 3-1 Q: if_else 문은 삼항 조건 연산자로 대체할 수 있다. (T/F)  -> T 
##### 3-2 Q: 삼항 조건 연산자 표현식은 if_else문으로 대체할 수 없다.(T/F) -> F

#### 3번 문제 코드 예시
```let x=  10;
let result = x % 2 ? '홀수' : '짝수'; // 이상적인 삼항 조건 연산자 코드
let result2 = if(x % 2) { return '홀수'; } else { return '짝수'; } // SyntaxError 
```

------

### 4. Q: 다음 코드의 실행 결과는 ? 고칠곳이 있다면 고치고, 이유를 설명해주세요.
```js
let poketmon = '피카츄';
let master;
switch (poketmon) {
    case '파이리':
        master = '웅이';
    case '꼬부기':
        master = '이슬이';
    case '피카츄':
        master = '지우';
    default:
        master = '로켓단';
}
console.log(master); // '로켓단' 출력
```
#### 왜 피카츄 -> 지우인데 , 로켓단이 출력될까? 
- switch문에서 case문이 실행되면 그 아래의 case문들도 실행되기 때문에 break문을 사용하여 중단시켜야한다.
- break문이 없어서 피카츄의 마스터가 지우로 잘 할당되었지만, 바로 default문이 실행되어 피카츄의 마스터가 로켓단으로 변경되었다.

-----

### 5. Q: 아래 코드에서 각 줄의 출력값과 그 이유를 설명해주세요
```js
let x ;
console.log(String(x));  // 'undefined' : x는 선언만 되어 있고 초기화되지 않았기 때문에 undefined
console.log(x.toString());  // TypeError : x는 선언만 되어 있고 초기화되지 않았기 때문에 TypeError 발생
```

-----

### 6. Q : 아래 코드에서 각 줄의 출력값과 그 이유를 설명해주세요

```js
'CAT' && 'DOG'; // 'DOG' : 논리 AND 연산자는 두 값이 모두 참일 때 뒤의 값을 반환한다.
'CAT' || 'DOG'; // 'CAT' : 논리 OR 연산자는 두 값 중 하나만 참이면 앞의 값을 반환한다.

false && 'DOG'; // false : 논리 AND 연산자는 두 값이 모두 참일 때 뒤의 값을 반환한다.
true || 'DOG';  // true : 논리 OR 연산자는 두 값 중 하나만 참이면 앞의 값을 반환한다.
```


-----

### 7. Q : 다음은 단축 평가로 에러를 방지하는 코드이다. <br/> let value = elem && elem.value; 이외에 다른 방법으로 에러를 방지할 수 있는 코드를 작성해주세요.

```js
let elem = null;
let value = elem && elem.value;  //  <- 해당 부분 

-> 다음으로 수정 

let value = elem?.value; // 옵셔널 체이닝 연산자를 사용하여 에러 방지
console.log(value);
let elem = {name: 'kevin'};
```

### 단축 평가?

- 논리 연산자를 사용하여 피연산자를 평가하는 과정에서 뒤의 피연산자를 평가하지 않는 것.
- 논리 AND 연산자(&&)는 두 피연산자가 모두 참일 때 뒤의 피연산자를 반환하고, 논리 OR 연산자(||)는 두 피연산자 중 하나만 참이면 앞의 피연산자를 반환한다.

#### 옵셔널 체이닝 연산자
- ?. 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티를 참조한다. (위의 예에서는 elem이 null이기 때문에 value에 undefined가 할당된다.)

------

### 8 Q: 자바스크립트에서 변수에 원시 값과 객체를 할당할 때 각각 메모리에 저장되는 값은 무엇인가요?

> 원시값을 할당한 변수는 원시 값 자체가 저장된다. <br/>객체를 할당하면 객체가 저장된 메모리(힙영역)를 참조하는 주소값이 저장된다.
