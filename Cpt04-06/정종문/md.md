### Q. [질문을 입력하세요]
<details>
<summary>A. [답변을 입력하세요]</summary>
[여기에 답변을 작성하세요]
</details>


### Q.동적타입이란? / js가 왜 동적타입인지?
<details>
<summary>정답</summary>
자바스크립트는 동적타입 언어라서 변수의 타입을 할당 시점에 결정하기 때문
</details>


```js
a=100;
b=200;
console.log(a);
console.log(b);

var a = 10;
let b = 20;
```
### Q. 위 코드의 결과는? ( a, b 출력 결과 )& 이유는 ?
<details>
<summary>정답</summary>
a =100
b =Uncaught ReferenceError: Cannot access 'b' before initialization

이유 : let은 호이스팅이 일어나지 않는다. -> 선언시에 undefined로 초기화가 되지 않는다.
var는 호이스팅이 일어나기 때문에 선언 전에 참조해도 undefined로 출력된다.
</details>
