명시적 타입 지정 없이 코드를 작성하면 컴파일 과정에서 다음과 같은 오류가 발생한다.

```tsx
let members = ["이권", "감장겸", "장도일"];

// [오류]
// [ts] 'number[]' 형식은 'string[]' 형식에 할당할 수 없습니다.
//      'number' 형식은 'string' 형식에 할당할 수 없습니다.
// let members: string[]
members = [9, 13, 26];
```

오류가 발생한 이유는 암시적으로 `members`변수에 설정된 데이터 타입이 `string[]`이기 때문이다.

`string`타입만으로 아이템이 채워진 초기 배열과 달리, `number`타입으로만 데이터를 채워 문제가 된다고 경고한다.

TS에서 배열 타입 할당 조건을 명시적으로 선언하는 방법은 다음과 같다.

```tsx
// 오직 숫자 아이템만 허용
let nums: number[] = [100, 101, 102];

// 오직 문자 아이템만 허용
let strs: string[] = ["ㄱ", "ㄴ", "ㄷ"];

// 오직 불리언 아이템만 허용
let boos: boolean[] = [true, false, true];

// 모든 데이터 타입을 아이템으로 허용
let anys: any[] = [100, "ㄴ", true];

// 특정 데이터 타입만 아이템으로 허용
let selects: (number | string)[] = [102, "ㅇ"];
```
