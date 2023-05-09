# 변수

## 변수의 생성 과정

1. 선언

```jsx
// 변수의 선언
let message;
```

1. 초기화

```jsx
// 변수의 초기화
let message; // undefinded
```

1. 할당

```jsx
// 변수의 할당
message = "hello"; // hello
```

## 변수의 종류

- var
- let
- const

### 각 변수의 특징

- var : 선언과 초기화가 동시에 이뤄짐 ⇒ 언제든 사용 가능 한 상태
- let : 초기화는 실제 코드에 도달 했을 때 적용 후 할당 ⇒ 블록 스코프 안으로 못들어가는 경우 에러
- const : 선언, 초기화, 할당 한번에 진행 ⇒ 즉 한번 할당하면 재할당이 불가하다(이미 주인 있음)

# hoisting

## var

### 예시

```jsx
console.log(name); // undefined

var name = "mike";
```

var : 선언과 초기화가 동시에 이뤄짐

⇒ 즉, 언제든 이용이 가능한 상태임

⇒ 호출 전 선언과 할당을 해도 undefined(초기화) 상태

### 변수의 호이스팅

실제로는 밑에 코드를 썻지만, 사실 호이스팅이 되어서 코드 최 상단부로 끌어올려진다(참고로, 이렇게 눈에 보이진 않지만 말로 표현하는 상태를 렉시컬 환경 즉 언어적 환경이라고 칭한다)

### 위의 코드 실행 과정

> 자바스크립트는 인터프리터 언어이기 때문에 파싱 후 위에서부터 한줄씩 실행된다

1. var 변수 호이스팅 후 선언 초기화 ⇒ 사용 가능한 상태(값을 할당 가능)
2. 출력부(console.log)를 만나서 undefined 추출(아직 값은 할당이 안된 상태이기 때문에 초기화된 상태가 출력됨)

```jsx
console.log(name); // undefined

var name = "mike";

console.log(name); // mike
```

1. 만약 밑에 출력부를 하나 더 만든다면 값이 할당 된 후이기 때문에 mike가 출력된다

## let, const

> let과 const도 호이스팅이 일어난다

```jsx
console.log(name); // error

let name = "mike";
```

이렇게 출력부 밑에 let을 선언하면 error가 나서 호이스팅이 안되는거 아니냐 생각하는 분들이 많은 것 같다

사실 호이스팅은 일어난다

단,

let 과 const와 var 의 큰 차이점음 TDZ(일시적 사각지대)의 영향을 받는다는 것이다.

### let

위의 코드로 예시를 들어보자

```jsx
console.log(name); // error

let name = "mike";
```

아까 말했듯이 let은 선언이 되면서 호이스팅이 일어나고 TDZ에 영향을 받는 상태가 된다

자바스크립트는 인터프리터 언어이기 때문에 한줄씩 실행 되는데

1. 아직 초기화가 안된 상태에서 출력부를 만난다
2. tdz(일시적 사각지대)에 의해서 let은 안보이게 된다

즉 호이스팅은 일어난다

### const + 꿀팁

const는 값의 할당을 동시에 해줘야하고 재할당이 불가하다

하지만 let은 값의 재할당이 가능하다 즉 언제 바뀌었는지 불안할 수 있다

처음엔 const로 변수를 지정 한 후 만약 조건문 안에서나 다른 재할당이 이루어져야 한다면 let을 사용해보자

(물론 하다보면 대충 감이 와서 const 와 let을 자유자재로 쓸 수 있긴하다)

## var을 쓰면 안되는 이유

> 전역 변수를 지양해주세요

```jsx
var a = 123;
console.log(a); // 123

var a = 567;
console.log(a); // 567
```

분명 a가 두번 선언 되었는데 에러가 나지 않고 모두 잘 출력된다

위에서 얘기했듯이 var은 호이스팅이 되자마자 초기화(사용가능한 상태)가 된 상태이기 때문에 계속 사용이 가능하다

이것만 보더라도 협업시 굉장히 심각한 문제가 생길 수 있다

### var는 함수 스코프로 움직인다

```jsx
var n = 0;
var i = 0;
for (i; i < 10; i++) {
  n += i;
}
console.log(n, i); // 45, 10
```

함수는 사실 강화 방어막이라고 생각하면 쉽다

하지만 var는 이런 강화 방어막을 제외한 모든 방어막(블록 스코프)에 마음대로 드나들 수 있다

위의 코드는 for 안에서 var로 선언한 코드이다 var로 선언하였기 때문에 i 도 유효한 값을 가지게 된다

전역 변수를 이렇게 남발 하다보면 변수가 엉켜서 큰일이 날 수 있다.

## 결론

사실 요즘은 es6 문법을 사용하기 때문에 var을 쓸 일이 없다

만약 옛날 코드가 필요하다면 BABEL을 사용하면 된다.

하지만 더 상위 개념인 클로저를 이해하려면 위의 개념을 필수로 알고 있어야 한다