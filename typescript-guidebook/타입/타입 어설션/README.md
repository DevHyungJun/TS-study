TS 프로그래밍을 하다 보면 타입 어설션을 사용해야 할 순간이 오게 된다.

타입 어설션은 컴파일러에게 “이 타입이 특정 타입임을 단언한다”라고 말하는 것과 같다.

다른 언어의 타입 캐스트와 비슷하지만, 특별한 검사나 데이터 재구성을 수행하지 않는다.

런타임 시, 영향을 받지 않으며 오직 컴파일 과정에서만 사용된다.

타입 어설션을 처리하는 방법은 2가지이다.

1번째 방법은 앵클 브라켓(`<>`) 문법을 사용하는 것이다.

```tsx
let assertion: any = "타입 어설션은 '타입을 단언'합니다.";

// 방법 1: assertion 변수의 타입을 string으로 단언 처리
let assertion_count: number = (<string>assertion).length;
```

2번째 방법은 `as`문법을 사용하는 것이다.

```tsx
let assertion: any = "타입 어설션은 '타입을 단언'합니다.";

// 방법 2: assertion 변수의 타입을 string으로 단언 처리
let assertion_count: number = (assertion as string).length;
```

두 방법 모두 결과는 동일하지만, JSX와 함께 사용하는 경우 `as`문법만 허용된다.
