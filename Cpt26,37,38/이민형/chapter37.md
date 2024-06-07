## 37장 Set과 Map

### Set

중복되지 않는 유일한 값들의 집합이다.

배열과 유사하지만 동일한 값 중복 포함x, 요소 순서에 의미 없음, 인덱스로 요소에 접근x과 같은 차이가 있다.

```javascript
const set1 = new Set([1, 2, 3, 3]); // 생성
console.log(set1.size); // 결과: 3, Set 객체 요소 개수는 size 프로퍼티를 사용한다.

set1.add(4); // 요소 추가
set1.has(2); // true, Set 요소 존재 여부 확인
set1.delete(2); // 요소 삭제
set1.clear(); // 요소 일괄 삭제
```

forEach 메서드로 요소 순회

Set 객체는 이터러블이다. ➡️ for ... of 문으로 순회할 수 있으며, 스프레드 문법과 배열 디스트럭처링의 대상이 될 수 있다.

- 집합 연산

```javascript
const setA = new Set([1, 2, 3, 4]);
const setB = new Set([2, 4]);

// 교집합
setA.intersection(setB);
// 합집합
setA.union(setB);
// 차집합
setA.difference(setB);
// 부분 집합과 상위 집합
setA.isSuperset(setB);
```

<hr />

### Map

Map 객체는 키와 값의 쌍으로 이루어진 컬렉션이다. 객체와 유사하다.

| 구분                   | 객체                    | Map 객체              |
| ---------------------- | ----------------------- | --------------------- |
| 키로 사용할 수 있는 값 | 문자열 또는 심벌 값     | 객체를 포함한 모든 값 |
| 이터러블               | ❌                      | ⭕                    |
| 요소 개수 확인         | Object.keys(obj).length | map.size              |

```javascript
const map = new Map(); // Map 객체 생성
```

- 요소 순회

  Map 객체는 이터러블이면서 동시에 이터레이터인 객체를 반환하는 메서드를 제공한다.

  - Map.prototype.keys
  - Map.prototype.values
  - Map.prototype.entries

<hr />
