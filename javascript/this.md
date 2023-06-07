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
### 3

생성자 안에서는 그 생성자 함수가 만드는 객체가 된다(instance 객체 라고함)

나중에 더 자세히 배워보자

```jsx
function machine() {
  this.name = "kim";
}

let obj = new machine();
console.log(obj); // machine { name: 'kim' }
```

### 4.

```jsx
<h1 id="button">test</h1>
  <button>버튼</button>
```

버튼이 있을때

```jsx
document.getElementById('button').addEventListener('click',function(){this})
```

this를 찾으면

```jsx
e.currunetTarget // 클릭이벤트가 일어나고 있는 곳
```

과 같은 뜻이다. 

```jsx
document.getElementById('button').addEventListener('click',function(e){
      let array = [1,2,3]
      array.forEach(function(a){console.log(this)}) // window
    })
```

이런 콜백함수에서 this는 window를 출력한다

만약 객체 안의 콜백함수에서 this를 호출하면 어떻게 될까

```jsx
let obj = {
  names: ["김", "이", "박"],
  sayName: function () {
    obj.names.forEach(function () {
      console.log(this);
    });
  },
};

obj.sayName(); //Object [global](window)
```

전역이다

하지만 화살표 함수를 쓰면 말이 달라진다 화살표 함수는 this를 재설정 하지 않고 부모의 this를 물려받아서 쓴다

```jsx
let obj = {
  names: ["김", "이", "박"],
  sayName: function () {
		console.log(this) // obj객체
    obj.names.forEach( () => {
      console.log(this); // obj객체
    });
  },
};

obj.sayName(); 
```

부모의 this인 obj객체를 그대로 받아온다

### this는 왜이래??

원래 화살표 함수가 없었을 때는 call, bind 같은 것으로 this를 직접 지정해주었다.

하지만 화살표 함수가 생기면서 편리해졌다
