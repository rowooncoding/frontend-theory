# 변수 총정리!

## 변수의 종류

1. var
2. let
3. const

## 변수 특징

1. 선언
2. 할당
3. 범위

## 정리

|        | var      | let | const |
| ------ | -------- | --- | ----- |
| 재선언 | O        | X   | X     |
| 재할당 | O        | O   | X     |
| 범위   | function | {}  | {}    |

## 선언

```jsx
var name
let name
const name
```

### 재선언

```jsx
var name = "kim";
var name = "park";

console.log(name); // park
```

```jsx
let name = "kim";
let name = "park";

console.log(name); // SyntaxError: Identifier 'name' has already been declared
```

var은 재선언이 가능하지만 let은 이미 선언되어 있다 라는 표시가 뜨면서 재선언이 불가능 하다.

const도 마찬가지임

## 할당

```jsx
name = "kim"; // 할당
```

### 재할당

```jsx
let name = "kim";

name = "park";

console.log(name); // park
```

var 과 let은 재할당이 가능하다

```jsx
const name = "kim";

name = "park";

console.log(name); // TypeError: Assignment to constant variable.
```

const는 불가능 하다.

단, object안의 값을 변경하는 것은 에러가 나지 않는다

```jsx
const user = {
  name: "kim",
};

user.name = "park";

console.log(user.name); // park
```

이건 변수를 재할당 한것이 아닌 객체 요소를 바꾼것 뿐임

만약 값이 고정된 객체를 만들고 싶다면?

```jsx
const user = {
  name: "kim",
};
Object.freeze(user);

user.name = "park";

console.log(user.name); // kim
```

바뀌지 않는다.

## 범위(scope)

```jsx
function callName() {
  var name = "kim"; // function 안에서만 존재함
  console.log(name); // kim
}
callName();

console.log(name); // name is not defined
```

var은 함수의 범위를 가진다.

함수 밖으로 나가면 없는 애임

let 과 const 는 범위가 더 좁다 함수 뿐만 아니라 모든 중괄호 안이 범위

```jsx
if (true) {
  let name = "park";
  console.log(name); // park
}

console.log(name); // name is not defined
```

## Hoisting 현상

```jsx
var age = 30; // 우리가 작성한 코드
```

이 코드를 javascript는 선언과 할당을 분리해서 해석한다

```jsx
var age; // 페이지 맨 위로 올려져서 해석함(호이스팅)

age = 30;
```

증명

```jsx
console.log(age); // undefined

var age = 30;
console.log(age); // 30
```

위의 콘솔은 값이 없는 undefined, 밑의 콘솔은 값이 할당이 되어서 30

하지만 let 과 const 는 다르게 작동한다

```jsx
console.log(age); // Cannot access 'age' before initialization

let age = 30;
console.log(age);
```

let 과 const도 분명히 호이스팅이 되긴 한다만,,, var처럼 초기화를 시켜주지않는다 undefined(초기화)는 뭔가 담을 준비를 하는건데 let 과 const는 선언과 할당 사이에 시간차가 있어서 에러가 난다.

즉, let 과 const는 좀 더 엄격하게 사용 가능하다.
