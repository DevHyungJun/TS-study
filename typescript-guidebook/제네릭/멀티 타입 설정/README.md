함수 또는 클래스에서 멀티 타입 변수를 활용할 수 있다.

두 개의 값을 쌍으로 받아 배열에 추가하는 함수를 제네릭으로 구현하면, 다양한 타입 조합을 안전하게 다룰 수 있다.

```tsx
// pairArray 사용자 정의 타입(Type Alias) 정의
type pairArray = [any, any][];

// 멀티 타입 T, M 설정된 함수 pushPairItem 정의
function pushPairItem<T, M>(arr: pairArray, item: [T, M]): pairArray {
  arr.push(item);
  return arr;
}

// piarArray 타입으로 설정된 data 배열 선언
const data: pairArray = [];

// 멀티 타입을 지정한 후, 적절한 타입을 포함하는 데이터 추가
pushPairItem<boolean, string>(data, [false, "false"]);
pushPairItem<number, string>(data, [2019, "이천십구년"]);
```

## 팩토리 함수 + 멀티 타입

클래스와 옵션을 멀티 타입으로 설정하여 처리하는 팩토리 함수가 있다고 가정해보자, 눈여겨 볼 부분은 클래스를 전달 받을 때 타입을 어떻게 설정하는가 이다.

```tsx
// 클래스 Model
class Model {
  constructor(public options: any) {}
}

// 팩토리 함수
function create<T, U>(C: { new (U): T }, options: U): T {
  return new C(options);
}

// create() 팩토리 함수에 Model, string[] 멀티 타입 설정
create<Model, string[]>(Model, ["class type"]);
```
