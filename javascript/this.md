# this

## this의 여러가지 뜻

### 1

![image](https://github.com/rowooncoding/frontend-theory/assets/114975279/a2632d53-6698-44b2-957d-0f0870018200)

window 객체가 나온다

![image](https://github.com/rowooncoding/frontend-theory/assets/114975279/8b6eb5fc-f2b8-456d-a709-db95ae8c00fb)

함수안에 넣고 실행해도 window 객체가 나온다

이 안에는 여러 함수들이 있다. ex) onchange 등등

엄격모드에서 사용하면 함수안에서 undefined가 나온다(별로 안중요함)

### 2

```jsx
let obj = {
  data: "kim",
  hello: function () {
    console.log(this);
  },
};

obj.hello(); // { data: 'kim', hello: [Function: hello] }
```

객체 안의 메소드에서 this를 호출하면 메소드가 동작하고 있는 객체를 출력한다.

```jsx
let obj = {
  data: {
    hello: function () {
      console.log(this);
    },
  },
};

obj.data.hello(); // { hello: [Function: hello] }
```

객체 안의 객체에서 메소드를 호출하면 메소드가 담겨있는 객체를 반환한다

즉, 객체 안에 메소드의 this는 호출한 대상을 반환한다

```jsx
**let obj = {
  data: {
    hello: () => {
      console.log(this);
    },
  },
};

obj.data.hello(); // window**
```

화살표함수에서의 this는 window를 가리킨다 왜냐하면 화살표 함수는 this를 찾지 않는다

안쪽에 호출부 this는 전역의 this를 찾아올라간다

### 참고

```jsx
let obj = {
  data: {
    hello() {
      console.log(this);
    },
  },
};

obj.data.hello();
```

객체 안에 메소드 쓸때는 이렇게 콜론 생략가능

# 전역의 비밀

함수나 변수를 전역에서 만들면 window에 보관한다

```jsx
{
  let obj = {
    data: {
      hello() {
        console.log(this);
      },
    },
  };

  obj.data.hello();
}
```

대충 이런식으로 되어있다고 생각하면 된다(실제로는 아니지만)

그래서

```
function sayHello() {
  console.log("hello");
}

sayHello(); // hello
```

이렇게 호출하는것과

![image](https://github.com/rowooncoding/frontend-theory/assets/114975279/1abf215c-b1c4-40ab-a258-7bf57e7bd26d)

이렇게 호출하는 것은 결과가 같다.
