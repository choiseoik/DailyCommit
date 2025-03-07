# 순수함수

- 같은 입력에 대해 항상 같은 출력
- 부수효과가 없다.(외부상태를 변경하지 않는다.)
- 외부 상태에 의존하지 않는다.

예를 들어 let f = n => 2\*n 이면 순수함수이다

순수 하지 않은 함수는 다음과 같은 방식을 사용한다

```js
let sharedStateNumber = 7;
let double;
let f = () => (double = 2 * sharedStateNumber);
f();
```

순수함수는 함수형 프로그래밍의 기초다. 함수형 프로그래밍은 상태를 가능한 한 최소화한다. 함수형 프로그래밍을 사용하는 프로그래머는 순수함수를 가장 선호하는데 순수 함수를 사용하면 공유 상태를 완화하여 개발 과정이 단순해지고 개별 로직을 분리할 수 있기 때문이다. 또한 테스트도 쉬워진다.
React 의 경우에는 상태비저장 컴포넌트를 더 많이 사용하고 의존성을 적게 가질수록 좋다는 것을 이미 알고 있다.

-리액트교과서 中-

---

## 함수형 프로그래밍 : 부수 효과를 없애고 순수 함수를 만들어 모듈화 수준을 높이는 프로그래밍 패러다임 이다.

- 부수효과 : 외부의 상태를 변경하는 것 또는 함수로 들어온 인자의 상태를 직접 변경하는 것
- 순수 함수 : 부수효과가 없는 함수 즉, 어떤 함수에 동일한 인자를 주었을 때 항상 같은 값을 리턴하는 함수

  - 외부의 상태를 변경하지 않는 함수이다.

## 순수 함수 (code)

```js
function add(a, b) {
  return a + b;
}
console.log(add(10, 5));
```

## 순수함수가 아닌것(code)

```js
var c = 10;
const add2 = (a, b) => a + b + c;

console.log(add2(19, 3));
c = 20;
console.log(add2(19, 3));
```

```js
var c = 20;
const add2 = (a, b) => {
  c = b;
  return a + b;
};
```

```js
var obj1 = { val: 10 };
function add4(obj, b) {
  obj.val += b;
}
```

객체를 인자로 받아서 그 상태를 변경 시키는 코드를 가지고 있기 때문에 순수 함수가 아니다.

```js
var obj1 = { val: 10 };
function add5(obj, b) {
  return { val: obj.val + b }; // obj의 val만 참조할 뿐 변경 없음
}
```

## 요약 및 정리

모듈화 수준이 높으면 재사용성이 높고 좋은 프로그래밍이라고 할 수 있다.

- 순수 함수는 평가 시점이 중요하지 않다.
- 순수 함수는 외부의 상태를 변경하지 않으면서 동일한 인자에 대해 항상 똑같은 값을 리턴하는 함수다.

## reference

[순수함수란](http://jeong-pro.tistory.com/23)
