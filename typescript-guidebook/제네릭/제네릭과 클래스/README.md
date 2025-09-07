클래스 정의 시, 제네릭을 사용하면 클래스를 사용해 객체를 생성할 때 사용자가 타입을 지정해 사용할 수 있다.

사용 방법은 클래스 이름 뒤에 `<T>`를 붙인다.

`T`는 관용적인 식별자로 다른 이니셜을 사용해도 무방하다.

```tsx
class Model<T> {
  private _data: T[] = [];

  constructor(data: T[] = []) {
    this._data = data;
  }

  get data(): T[] {
    return this._data;
  }

  add(item: T): void {
    this._data.push(item);
  }

  remove(index: number): void {
    this._data.splice(index, 1);
  }

  item(index: number): T {
    return this._data[index];
  }

  clear(): void {
    this._data = [];
  }
}
```

사용 예시로 문자 데이터만 허용하는 `Model`객체 인스턴스를 사용하고자 한다면, 클래스를 통해 객체를 생성하는 코드에 제네릭 타입 변수 값을 `<string>`으로 설정해 사용한다.

설정된 타입이 아닌 다른 타입이 아이템에 사용되면 컴파일 과정에서 오류 메시지를 출력한다.

즉, 클래스 사용 과정에서 사용자가 설정한 타입만 사용할 수 있도록 제한한다.

```tsx
const stringModel = new Model<string>();

stringModel.add("흔들의자");

// [오류]
// '2018' 형식의 인수는 'string' 형식의 매개 변수에 할당될 수 없습니다.
stringModel.add(2018);
```

하지만 TS 프로그래밍 과정에서 부득이하게 정해진 타입이 아닌, 경우를 사용해야 하는 경우가 종종 발생한다.

이런 경우 타입 어설션 문법을 사용해 컴파일 과정의 타입 검사를 우회할 수 있지만, 꼭 필요한 경우에만 사용하는 것이 좋다.

```tsx
stringModel.add(2018 as any);

// 또는

stringModel.add(<any>2018);
```
