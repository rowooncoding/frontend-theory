# 함수 업그레이드 하기

## 함수 사용법

```jsx
function add(a, b) {
  console.log(a + b);
}

add(a, b);
```

## default 파라미터

```jsx
**function add(a, b = 10) { // b의 기본값을 10으로 해주세요
  console.log(a + b);
}

add(a, b);**
```

```jsx
function add(a, b = 10) {
  console.log(a + b);
}

add(1, 2); // 3
```

특징은 값이 없으면 10이지만 값이 들어가면 10이 아니고 인자가 들어간다.

```jsx
function add(a, b = 2 * 5) {
  console.log(a + b);
}

add(1, 2); // 3
```

수학 연산도 가능하다

```jsx
function add(a, b = 2 * a) {
  console.log(a + b);
}

add(1); // 3
```

인자를 연산식의 변수로 넣을 수도 있다.

```jsx
function myFunction() {
  return 10;
}

function add(a, b = myFunction()) {
  console.log(a + b);
}

add(1, 2); // 3
```

함수를 넣을 수도 있다.

## argument

> 모든 파라미터를 한번에 다루고 싶을 때.

```jsx
**function add(a, b, c) {
  console.log(arguments);
}

add(1, 2, 3); // [Arguments] { '0': 1, '1': 2, '2': 3 }**
```

```jsx
function add(a, b, c) {
  console.log(arguments[0]);
}

add(1, 2, 3); // 1
```

각각 index 번호로 다룰 수 있다.

**파라미터가 굉장히 많을 때 유용하다**
