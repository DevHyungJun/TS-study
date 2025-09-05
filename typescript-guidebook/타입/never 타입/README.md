`never`는 일반적으로 함수의 리턴 타입으로 사용된다.

함수의 리턴 타입으로 `never`가 사용될 경우, 항상 오류를 출력하거나 리턴 값을 절대로 내보내지 않음을 의미한다.

이는 무한 루프에 빠지는 것과 같다.

```tsx
// 항상 오류 발생
function invalid(message: string): never {
  throw new Error(message);
}

// never 타입을 결과 추론(Inferred)
function fail() {
  return invalid("실패");
}

// 무한 루프
function infiniteAnimate(): never {
  while (true) {
    infiniteAnimate();
  }
}
```

`never`타입을 지정한 변수에 `never`가 아닌 타입은 할당할 수 없다.

```tsx
let never_type: never;

// 오류 발생: 숫자 값을 never 타입 변수에 할당할 수 없습니다.
never_type = 99;

// 함수의 반환 값이 never 타입 이기 때문에 오류가 발생하지 않습니다.
never_type = (function (): never {
  throw new Error("ERROR");
})();
```
