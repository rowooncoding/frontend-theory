# **primitive/reference data type**

## **primitive data type**

> 변수에 값이 그대로 저장됨

예) 문자, 숫자 자료형

## **reference data type**

> 객체, 배열

### 객체, 배열은 값이 저장되지 않는다.

```jsx
let arr = [1, 2, 3, 4];

let arr2 = arr;
```

변수에 참조가 저장된다(저번에 배웠다)

참조에 의한 복사는 저번 글에 자세히 설명 했으니 생략하겠음

### 객체 재할당

```jsx
let name1 = { name: "김" };

function change(obj) {
  obj = { name: "park" };
}

change(name1);

console.log(name1); // "김"
```

객체의 프로퍼티를 재할당 하는 함수를 사용했는데 프로퍼티가 바뀌지 않았다

### 왜?

파라미터 ⇒ 변수 생성, 할당과 같다

```jsx
change(name1);
```

이것은

```jsx
change((obj = name1));
```

이렇게 파라미터에 할당하는 것과 같다.

즉 위의 코드는

```jsx
{
  name: "김";
}
```

이라는 메모리를 name1이라는 변수와 obj라는 변수가 동시에 참조하고 있는 것이다.

그러다가 위의 코드 change 함수에서 obj에게 새로운 객체를 할당하고 있기 때문에

name1과 change는 각각 다른 객체를 가리키고 있는 것이다.
