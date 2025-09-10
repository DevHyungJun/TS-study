데코레이터는 ECMAScript에 새롭게 제안된 기능이며, TS의 실험적 기능으로 클래스 선언과 멤버에 대한 주석과 메타 프로그래밍 구문을 모두 추가 할 수 있는 방법을 제공한다.

## 데코레이터 사용 설정

데코레이터를 TS에서 사용하려면 `tsconfig.json`설정 `experimentalDecorators`값을 `true`로 설정해야 한다.

환경 설정 없이 데코레이터를 사용하려면 컴파일 과정에서 오류 메시지를 출력한다.

```tsx
{
  "compilerOptions": {
  ...
  "experimentalDecorators": true,
  ...
  }
}
```

데코레이터는 차후 릴리즈 시, 변경 될 수 있는 실험 기능이다.
