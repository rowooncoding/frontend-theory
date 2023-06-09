# 모든 괄호를 없애주는 Spread Operator(전개연산자)

## 사용법

```jsx
let arr = ["hello", "world"];
console.log(arr); // [ 'hello', 'world' ]
console.log(...arr); // hello world
```

괄호를 다 풀어서 적어준다.

문자에도 활용 가능함

```jsx
let str = "hello";

console.log(str); // hello
console.log(...str); // h e l l o
```

한 단어씩 띄워서 써준다

## 활용

```jsx
let a = [1, 2, 3];
let b = [4, 5];

let c = [...a, ...b];
console.log(c); // [ 1, 2, 3, 4, 5 ]
```

쉽게 합치거나 복사가 가능하다.

```jsx
let a = [1, 2, 3];

let b = [4, ...a, 5];
console.log(b); // [ 4, 1, 2, 3, 5 ]
```

중간에도 넣을 수 있다.

### Deep copy

전개 연산자의 장점이 잘 들어난다

복사에는 값복사와 참조에 의한 복사가 있다.

1. 참조에 의한 복사

```jsx
let a = [1, 2, 3];

let b = a;

a[3] = 4;

console.log(a); // [ 1, 2, 3, 4 ]
console.log(b); // [ 1, 2, 3, 4 ]
```

우리는 b는 건들지 않았지만 서로 참조하고 있기 때문에 동시에 값이 바뀐다.

1. 값 복사

우리가 흔히 아는 복사다

```jsx
let a = [1, 2, 3];

let b = [...a];

a[3] = 4;

console.log(a); // [ 1, 2, 3, 4 ]
console.log(b); //  [ 1, 2, 3 ]
```

a와 b 어레이는 다른 값이다.

나중에 자세히 다룰것임.

### 오브젝트 합치기

```jsx
let obj1 = {
  a: 1,
  b: 2,
};

let obj2 = {
  ...obj1,
  c: 3,
};

console.log(obj2); // { a: 1, b: 2, c: 3 }
```

복사도 배열이랑 똑같이 하면 된다

### 함수파라미터 넣을때

```jsx
function add(a, b, c) {
  return a + b + c;
}

let arr = [10, 20, 30];

add(...arr); // 60
```
