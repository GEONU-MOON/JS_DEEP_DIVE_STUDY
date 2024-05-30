## 21장 빌트인 객체

### 자바스크립트 객체

- 표준 빌트인 객체

  Object, String, Number, Boolean 등 애플리케이션 전역의 공통 기능을 제공하는 객체

- 호스트 객체

  자바스크립트 실행 환경에서 추가로 제공하는 객체

- 사용자 정의 객체

  사용자가 직접 정의한 객체

### 전역 객체

전역 객체는 어떤 객체에도 속하지 않은 모든 빌트인 객체의 최상위 객체다.

- 브라우저 환경: window

- Node.js 환경: global

let, const로 선언한 변수는 전역 객체의 프로퍼티가 아니다.

#### 빌트인 전역 프로퍼티

- Infinity

  무한대

- NaN

  숫자가 아님(Not-a-Number)을 나타내는 숫자값

  Number.NaN 프로퍼티와 같다.

- undefined

#### 빌트인 전역 함수

- eval

  eval 함수를 통해 사용자로부터 입력받은 콘텐츠를 실행하는 것은 보안에 매우 취약하므로 eval 함수의 사용은 금지해야 한다.

- isFinite

  전달받은 인수가 정상적인 유한수인지 검사

- isNaN

  전달받은 인수가 NaN인지 검사

- parseFloat

  전달받은 문자열을 실수로 변환

- parseInt

- encodeURI / decodeURI

- encodeURIComponent / decodeURIComponent

#### 암묵적 전역

선언하지 않은 식별자에 값을 할당하면 전역 객체의 프로퍼티가 되는 현상을 말한다.

암묵적 전역으로 생성된 프로퍼티는 선언과 초기화가 동시에 진행되므로 변수 호이스팅이 발생하지 않는다.
