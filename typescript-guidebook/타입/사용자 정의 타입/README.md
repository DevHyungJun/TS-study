복잡한 타입을 매번 설정하는 것은 번거로운 작업이다.

`Dom`,`y9`변수에 할당될 객체의 각 속성별 타입 설정을 살펴보면 매우 복잡하다.

```tsx
let Dom: {
  version: string;
  el: (selector: string) => void;
  css: (prop: string) => void;
} = {
  version: "0.0.1",
  el() {},
  css() {},
};

let y9: {
  version: string;
  el: (selector: string) => void;
  css: (prop: string) => void;
} = {
  version: "0.0.2",
  el() {},
  css() {},
};
```

이러한 경우 복잡한 타입을 사용자 정의하여 재사용하기 용이하도록 TS는 지원한다.

타입 별칭을 정의하려면 `type`키워드를 사용한다.

```tsx
// 사용자 정의 타입 operation 정의
// 타입 별칭(Type Alias)
type operation = {
  data: number[];
  output: (num: number) => number[];
};

// 사용자 정의 타입 operation 적용 예시
let sum: operation = {
  data: [10, 30, 60],
  output(num) {
    return this.data.map((n) => n + num);
  },
};

let multiply: operation = {
  data: [110, 230, 870, 231],
  output(num) {
    return this.data.map((n) => n * num);
  },
};
```
