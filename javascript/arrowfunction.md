# 화살표 함수는 과연 일반 함수의 대체일까

## 함수 만드는 방법

```jsx
function foo() {} // 1
let foo = () => {}; // 2
```

2번 화살표 함수는 es6에 만들어진 함수를 편하게 쓸 수 있는 방법

## 함수 만드는 이유

1. 코드들을 기능으로 묶고 싶을 때
2. 입출력하는 기계를 만들고 싶을 때

## 장점

```jsx
let foo = () => {};
```

### 1. 직관적

```jsx
let add = (a) => {
  return a + 5;
};
```

a를 넣으면 a+5를 출력해줘. 직관적임

### 2. 소괄호 생략 가능

```jsx
let add = (a) => {
  return a + 5;
};
```

파라미터가 하나라면 소괄호가 생략 가능하다

### 3. 중괄호 생략 가능

```jsx
let add = (a) => a + 5;
```

만약 return 하는 것이 한줄이라면 중괄호와 return을 생략 가능하다

## 그럼 화살표 함수만 써?

그럴 수 없다.

앞에서 배운것 처럼 this를 사용할때 화살표 함수는 부모의 this를 받기 때문에 결과가 이상해질 수 있다.

예를 들면

```jsx
document.getElementById("button").addEventListener("click", function (e) {
  console.log(this);
});
```

```jsx
document.getElementById("button").addEventListener("click", (e) => {
  console.log(this);
});
```

이것의 this결과는 다르다

---

## 추가

### setTimeout()

> 특정 코드나 함수를 n초 후에 실행하고 싶을 때 사용한다.

### 활용법

```jsx
setTimeout(() => {
  console.log("안녕");
}, 1000); // 1초 후에 안녕히 적힌다
```

함수를 넣을 수도 있다.

```jsx
function foo() {
  console.log("안녕");
}

setTimeout(foo, 1000);
```

위에가 더 간단한듯!
