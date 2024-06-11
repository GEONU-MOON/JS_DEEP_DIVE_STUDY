## 39장 DOM

> DOM(Document Object Model)
>
> HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API(프로퍼티와 메서드)를 제공하는 트리 자료구조

### DOM tree

DOM에서 모든 요소, 어트리뷰트, 텍스트는 하나의 객체이며 Document 객체의 자식이다.

DOM tree의 진입점은 document 객체이며, 최종점은 요소의 텍스트를 나타내는 객체이다.

- DOM tree는 네 종류의 노드로 구성된다.

  1. Document Node
     트리 최상위 존재

  2. Element Node
     HTML 요소

  3. Attribute Node
     HTML 요소의 어트리뷰트

  4. Text Node
     HTML 요소의 텍스트

<hr />

### 요소 노드 취득

#### id 이용

- Document.prototype.getElementById

  인수로 전달된 id 값을 갖는 첫 번째 요소 노드만 반환한다.

#### class 이용

- Document.prototype/Element/prototype.getElementByClassName

  인수로 전달된 class 어트리뷰트 값을 갖는 모든 요소들을 탐색하여 반환한다.

<hr />

### HTMLCollection과 NodeList

- HTMLCollection

  노드 객체의 상태 변화를 실시간으로 반영하는 live Dom 컬렉션 객체

- NodeList

  실시간으로 노드 객체의 상태 변경을 반영하지 않는 non-live 객체

_노드 객체의 상태 변경과 상관없이 안전하게 DOM 컬렉션을 사용하려면 HTMLCollection이나 NodeList 객체를 배열로 변환하여 사용하는 것을 권장한다._

<hr />

### DOM 조작

DOM 조작에 의해 DOM에 새로운 노드가 추가되거나 삭제되면 리플로우와 리페인트가 발생한다.

> 리플로우: 레이아웃을 다시 계산하는 것
>
> 리페인트: 재결합된 렌더 트리를 기반으로 다시 페인트 하는 것

#### innerHTML

HTML 마크업이 파싱되어 DOM에 반영된다.

사용자로부터 입력 받은 데이터를 그대로 innerHTML 프로퍼티에 할당하는 것은 **크로스 사이트 스크립팅 공격(XSS)**에 취약하다.

> 크로스 사이트 스크립팅 공격(XSS)
>
> 웹사이트 관리자가 아닌 이가 웹 페이지에 악성 스크립트를 삽입하는 공격. 사용자의 세션을 가로채거나, 웹사이트를 변조하거나, 악의적 콘텐츠를 삽입하거나, 피싱 공격을 진행할 수도 있다.

<hr />

### 노드 복사

Node.prototype.cloneNode

노드의 사본을 생성하여 반환한다.

- 매개변수 deep에 true ➡️ 노드 깊은 복사(자식까지 복사)

- 매개변수 deep에 false 또는 생략 ➡️ 노드 얕은 복사

<hr />

### HTML 어트리뷰트 vs. DOM 프로퍼티

HTML 어트리뷰트는 H요소 노드의 초기 상태를 관리한다.

DOM 프로퍼티는 요소 노드의 최신 상태를 관리한다.

<hr />
