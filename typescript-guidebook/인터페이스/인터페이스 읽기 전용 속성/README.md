일부 속성은 처음 만들어 질 때 외에는 수정할 수 없도록 설정하고 싶을 수 있다.

그런 경우 속성의 이름 앞에 readonly를 넣어 설정할 수 있다.

```tsx
interface Notebook {
  readonly CPU: string;
  readonly RAM: string;
}
```

인터페이스 이행이 지정된 객체의 readonly로 지정된 속성을 할당 이후, 임의로 변경을 시도하면 오류가 발생한다.

```tsx
let mackbook: Notebook = {
  CPU: "2.9GHz 코어 i9",
  RAM: "32GB",
};

// [오류]
// 'RAM'은 읽기 전용 속성 또는 상수로 변경할 수 없습니다.
// (property) Notebook["RAM"]: string
macbook.RAM = "128GB";
```
