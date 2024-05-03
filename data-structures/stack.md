## Stack(스택)

> 아래 두 가지 연산을 가진 요소들의 집합인 추상 자료형 (LIFO(Last In, First Out) 구조)

- **push**는 집합에 요소를 추가하는 것
- **pop**은 아직 제거되지 않은 가장 최근에 추가된 요소를 제거
- **peek** 연산은 스택을 수정하지 않고 최상단 요소에 접근 

![stack](https://github.com/kwhong95/js_study/assets/70752848/5f1767bb-3520-44af-8ccf-aa5b4b5ff89a)

### 활용 예시 

사용자가 어떤 작업을 수행했을 때(예: 텍스트 입력, 요소 이동 등), 이전 상태로 되돌아가기 위해 **Stack**을 사용하여 사용자의 작업 기록을 관리할 수 있습니다.

  예를 들어, 사용자가 입력한 텍스트를 스택에 저장하고, 사용자가 UNDO 기능을 요청했을 때, 가장 최근에 추가한 텍스트를 스택에서 제거하고 해당 상태로 돌아가는 방식으로 UNDO 기능을 구현할 수 있습니다.


### 활용 예시 코드 구현

```ts
  // Stack 클래스: Stack 자료 구조를 구현하는 클래스
class Stack {
  private items: any[];

  constructor() {
    this.items = [];
  }

  push(element: any) {
    this.items.push(element);
  }

  pop() {
    if (this.items.length === 0) {
      return "Stack is empty";
    }
    return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}

// UNDO 기능을 구현하는 예시
const undoStack = new Stack();

// 사용자가 입력한 텍스트를 스택에 추가
undoStack.push("First text");
undoStack.push("Second text");

// UNDO 기능 실행
const lastUndo = undoStack.pop(); // "Second text"
console.log("UNDO:", lastUndo);

// 현재 스택 상태 확인
console.log("Current stack:", undoStack);
```

### 시간 복잡도

| peek(최상위 값 참조) | search | push | pop |
| :---: | :---: | :---: | :---: |
| $O(1)$ | $O(n)$ | $O(1)$ | $O(1)$ |

### 공간 복잡도

$O(n)$