인터페이스는 JS와 같은 동적 타입 언어 환경에서는 다뤄지지 않는다.

하지만 정적 타입 언어인 TS에서는 타입 검사가 요구되므로 인터페이스를 지원한다.

`interface`키워드를 사용해 다음과 같이 정의한다.

```tsx
// 인터페이스 Button 정의
interface ButtonInterface {
  onInit(): void;
  onClick(): void;
}
```

사용자 정의 타입(Type Alias)과 유사해보인다.

```tsx
type ButtonType = {
  onInit(): void;
  onClick(): void;
};
```

다소 비슷해보이지만 사용자 정의 타입이 할 수 없는 것을 인터페이스는 할 수 있다.

첫 번째로 인터페이스는 선언을 병합할 수 있다는 점이다.

```tsx
interface ButtonInterface {
  onInit():void;
  onClick():void;
}

...

interface ButtonInterface {
  onToggle():void;
}
```

반면 사용자 정의 타입은 선언이 중복되면 오류이다.

```tsx
type ButtonType = {
  onInit(): void;
  onClick(): void;
};

// [오류]
// 'ButtonType' 식별자가 중복되었습니다.
type ButtonType = {
  onToggle(): void;
};
```
