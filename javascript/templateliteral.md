# 자바스크립트가 문자를 다루는 특별한 방법

## 백틱

```jsx
let name = `hello`;
```

## 백틱의 장점

1. 엔터키 가능
2. 중간중간 변수 넣기 쉽다

   1. 옛날방식

   ```jsx
   let name = "민수";
   let str = "안녕하세요 저는 " + name + "입니다";
   console.log(str); // 안녕하세요 저는 민수입니다
   ```

   b. 요즘 방식

   ```jsx
   let name = "민수";
   let str = `안녕하세요 저는 ${name} 입니다`;
   console.log(str); // 안녕하세요 저는 민수입니다
   ```

   html에서 변수 넣기 좋다(다이나믹 라우트 할때 매우 유용)

3. tagged literal

```jsx
function tagged(strings, variables) {
  console.log(strings); // [ '안녕하세요 저는 ', ' 입니다' ]
  console.log(variables); // 민수
}
tagged`안녕하세요 저는 ${name} 입니다`;
```

문자를 단어 기준으로 나눠서 배열에 넣어주고 변수를 따로 모아준다

활용해보자

```jsx
function tagged(strings, variables) {
  let newString = strings[1] + strings[0];
  console.log(newString); //  입니다안녕하세요 저는
}
tagged`안녕하세요 저는 ${name} 입니다`;
```

문자를 단어별로 배열에 넣기 때문에 index를 사용하여 장난을 칠 수 있다.
