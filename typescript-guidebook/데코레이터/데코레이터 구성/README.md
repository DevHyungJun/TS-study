데코레이터는 하나 이상 연결해 사용할 수 있다.

멀티 데코레이터는 수평 또는 수직 나열하여 사용할 수 있다.

```tsx
// 수평 나열
@Size
@Color
class Button {}
```

```tsx
// 수직 나열
@Size
@Color
class Button {}
```

## 실행 흐름(평가/호출)

데코레이터의 실행 흐름은 다음 순으로 처리된다.

1. 각 데코레이터 표현식은 위에서 아래 방향으로 평과된다.
2. 결과는 아래에서 위로 함수를 호출한다.

데코레이터 팩토리를 사용해 멀티 데코레이터의 실행 흐름을 살펴보는 것이 이해가 빠를 것이다.

```tsx
// Size 데코레이터 팩토리
function Size() {
  console.log("Size(): 평가됨");
  // Size 데코레이터
  return function (target: any, prop: string, desc: PropertyDescriptor) {
    console.log("Size(): 실행됨");
  };
}

// Color 데코레이터 팩토리
function Color() {
  console.log("Color(): 평가됨");
  // Color 데코레이터
  return function (target: any, prop: string, desc: PropertyDescriptor) {
    console.log("Color(): 실행됨");
  };
}

// Button 클래스 정의
class Button {
  // 메서드에 멀티 데코레이터 적용
  @Size()
  @Color()
  isPressed() {}
}
```

console에 출력되는 결과는 다음과 같다.

```tsx
Size(): 평가됨
Color(): 평가됨
Color(): 실행됨
Size(): 실행
```
