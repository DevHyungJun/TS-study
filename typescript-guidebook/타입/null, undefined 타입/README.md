JS에서 `null`,`undefined`는 데이터 타입이자 하나의 값이다.

TS에서도 하나의 타입으로 처리되며 다음과 같이 사용할 수 있다.

```tsx
let nullable: null = null;
let undefinedable: undefined = undefined;
```

하지만 `null`로 명시적 타입이 설정된 변수에 `null`이 아닌 값이 할당되면 다음과 같은 오류를 출력한다.

```tsx
// [오류]
// [ts] 'undefined' 형식은 'null' 형식에 할당할 수 없습니다.
// let nullable: null
nullable = undefined;
```

이렇게 엄격하게 오류를 뱉는 이유는 `tsconfig.json`에 다음과 같이 설정되어 있기 때문이다.

설정 값을 `false`로 설정할 경우 위와 같은 오류가 발생하지 않는다.

```tsx
"strictNullChecks": true, /* 엄격한 null 검사 사용 */
```

참고로 `“strictNullChecks”: true`설정 시, 모든 데이터 타입은 `null`, `undefined`를 할당 받을 수 없다. 그러므로 아래와 같은 코드는 오류를 출력한다.

```tsx
// [오류]
// [ts] 'null' 형식은 'string' 형식에 할당할 수 없습니다.
// let assign_name: string
let assign_name: string = null;

if (!assign_name) {
  assign_name = "미네랄";
}
```

이 문제를 해결하려면 `any`또는 유니온(`|`) 타입을 사용해야 한다.

하지만 `any`를 사용하면 `string`타입으로 특정 짓는 것이 아니므로 유니온 타입을 사용하는 것이 보다 적절하다.

```tsx
// let assign_name:any = null;
let assign_name: string | null = null;

if (!assign_name) {
  assign_name = "미네랄";
}
```

만약 아래와 같이 코드를 작성했을 때 `null`,`undefined`를 항상 서브 타입으로 할당 가능하게 하려면, 즉 오류를 출력하지 않으려면 `tsconfig.json`설정에서 `“strictNullChecks”`값을 `false`로 설정하면 된다.
