`private`접근 제어자를 사용해 `constructor()`앞에 붙이면 `new`키워드를 통해 인스턴스를 생성하지 못하도록 제한할 수 있다.

대신 공개된 스태틱 메서드 `getInstance()`를 통해 오직 한 번만 인스턴스를 생성할 수 있다.

이를 싱글턴 패턴이라 부른다.

```tsx
class OnlyOne {
  private static instance: OnlyOne;

  public name: string;

  // new 클래스 구문 사용 제한을 목적으로
  // constructor() 함수 앞에 private 접근 제어자 추가
  private constructor(name: string) {
    this.name = name;
  }

  // 오직 getInstance() 스태틱 메서드를 통해서만
  // 단 하나의 객체를 생성할 수 있습니다.
  public static getInstance() {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne("싱글턴 객체");
    }
    return OnlyOne.instance;
  }
}

/* 인스턴스 생성 ------------------------------------------------ */

// [오류]
// [ts] 'OnlyOne' 클래스의 생성자는 private이며 클래스 선언 내에서만 액세스할 수 있습니다.
// constructor OnlyOne(name: string): OnlyOne
let bad_case = new OnlyOne("오류 발생");

let good_case = OnlyOne.getInstance();
```

컴파일 된 ES5 코드를 살펴보면 싱글턴 패턴과 상관 없이 여러 차례 인스턴스를 생성할 수 있따.

하지만 JS는 객체 자체가 싱글턴이 될 수 있다.

```tsx
// 컴파일 코드
var OnlyOne = /** @class */ (function () {
  function OnlyOne(name) {
    this.name = name;
  }
  OnlyOne.getInstance = function () {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne("싱글턴 객체");
    }
    return OnlyOne.instance;
  };
  return OnlyOne;
})();

let only_one = new OnlyOne("오류 발생"); // 정상 작동
let special_one = new OnlyOne("스페셜 원"); // 새로운 인스턴스 생성!
let normal_one = new OnlyOne("노멀 원"); // 새로운 인스턴스 생성!!
```
