코드 양만 보면 굳이 TS를 써야 할까 싶지만, TS를 사용하면 JS와 달리 코드 작성 과정에서 코드를 실시간으로 디버깅할 수 있어 매우 편리하다.

또한 TS는 JS로 변환(트랜스파일) 되어야 실행 가능한 트랜드파일 언어이기에 TS 코드가 JS로 변환될 때 타입 정보는 사라지고, 실행 가능한 순수 JS 코드만 남게된다.

핵심 이유는 다음과 같다.

- 정적 타입 검사
- 자동 완성 & IDE 지원
- 코드 안정성 향상
- 리팩토링 편리

## JS + 유효성 검사

JS에서도 유효성 검사를 작성할 수 있지만 다음과 같이 직접 검사 과정을 작성하는 것은 매우 번거롭고 불편한 일이다.

```jsx
function ellipsisText(text, limit, symbol = "...") {
  if (typeof text !== "string")
    throw new Error("1번째 전달인자 유형은 문자여야 함");
  if (typeof limit !== "number")
    throw new Error("2번째 전달인자 유형은 숫자여야 함");
  if (typeof symbol !== "string")
    throw new Error("3번째 전달인자 유형은 문자여야 함");
  return `${text.slice(0, limit - 1)}${symbol}`;
}
```

## TS

TS로 작성된 코드는 앞서 작성한 JS 함수보다 복잡해보이지만, 작성 후 함수 실행 시, 컴파일 과정에서 실시간으로 타입을 검사하므로 디버깅이 쉽고 프로그램의 안정성을 보장한다.

```tsx
function ellipsisText(
  text: string,
  limit: number,
  symbol: string = "..."
): string {
  return `${text.slice(0, limit - 1)}${symbol}`;
}
```

TS를 사용한 선언 과정에서 설정된 타입에 의해 실시간으로 오류를 표시한다.
