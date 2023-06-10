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

## rest 파라미터

> 사실 argument는 옛날 문법임!, react에서 props전달할때 많이 쓴다

arguments는 특정 파라미터만 사용하려면 반복문 써야함

```jsx
function myFunction(...rest) {
  console.log(rest);
}

myFunction(1, 2, 3, 4, 5, 6); // [ 1, 2, 3, 4, 5, 6 ]
```

파라미터 자리에 오는 모든 파라미터를 배열 안에 보관해준다

만약 특정 파라미터를 찝어내고 싶다면.

```jsx
function myFunction(a, b, ...rest) {
  console.log(rest);
}

myFunction(1, 2, 3, 4, 5, 6); // [ 3, 4, 5, 6 ]
```

이렇게 따로 써주면 된다.

### 응용 : 모든 인자를 하나씩 뽑아보자

```jsx
function myFunction(...rest) {
  for (let i = 0; i < rest.length; i++) {
    console.log(rest[i]);
  }
}

myFunction(1, 2, 3, 4, 5, 6);
```

반복문 돌리기

### 특징

```jsx
function myFunction(...rest,a,b) {
  for (let i = 0; i < rest.length; i++) {
    console.log(rest[i]);
  }
}

myFunction(1, 2, 3, 4, 5, 6);
```

rest 파라미터 뒤에 인자 쓰는거 안됨

```jsx
function myFunction(...rest,..rest1) {
  for (let i = 0; i < rest.length; i++) {
    console.log(rest[i]);
  }
}

myFunction(1, 2, 3, 4, 5, 6);
```

rest 파라미터 여러번 쓰는거 안됨
