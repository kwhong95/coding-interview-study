## Queue (큐)

> 선입 선출(FIFO) 자료구조 

큐 내부의 엔티티들은 순서를 유지하며 컬렉션의 가장 뒷 부분에 엔티티를 추가하는 인큐(enqueue),
  컬렉션의 가장 앞에 위치한 엔티티를 제거하는 디큐(dequeue) 작업을 수행합니다.

![queue](https://github.com/kwhong95/coding-interview-study/assets/70752848/2f094cba-9e02-4f42-b742-cfecf19762b8)


#### 활용 예시

> 이벤트 처리(Event Handling) 메커니즘

웹 어플리케이션에서 발생하는 다양한 이벤트들을 순서대로 처리하고 관리할 때 Queue 자료구조를 사용할 수 있습니다.
  예를 들어 사용자의 클릭, 입력, 타이머 등의 다양한 이벤트들이 발생하는 웹 페이지에서 이벤트 처리를 관리 할 때 Queue를 사용할 수 있습니다. 이벤트가 발생하면 해당 이벤트를 Queue에 추가하고, FIFO(First-In-First-Out) 방식으로 이벤트를 처리하여 순차적으로 실행할 수 있습니다. 

  또 다른 예시로는 데이터를 비동기적으로 처리할 때 Queue를 활용할 수 있습니다. 예를 들어, 웹 어플리케이션이 서버로부터 비동기적으로 데이터를 받아오는 경우, 받아온 데이터를 Queue에 추가하고 하나씩 처리하여 데이터 순서를 보장할 수 있습니다.



#### 활용 예시 코드

```ts
class Event {
  public name: string

  constructor(name: string) {
    this.name = name; // 이벤트의 이름
  }
}

class EventQueue {
  private queue: Event[]

  constructor() {
    this.queue = [] // 이벤트를 저장할 Queue 배열
  }

  // 이벤트를 Queue에 추가하는 메서드
  public addEvent(event: Event) {
    this.queue.push(event)
    console.log(`이벤트 추가: ${event.name}`)
  }

  // Queue에서 이벤트를 꺼내 처리하는 메서드
  public processEvents() {
    while (this.queue.length > 0) {
      const evnet = this.queue.shift()
      console.log(`이벤트 처리: ${event.name}`)
    }
    console.log('모든 이벤트 처리 완료')
  }
}

// 이벤트 처리 메커니즘을 사용하는 예시
const eventQueue = new EventQueue()

eventQueue.addEvent(new Event('click'))
eventQueue.addEvent(new Event('input'))
eventQueue.addEvent(new Event('load'))

eventQueue.processEvents();
```

#### 시간 복잡도

| Search | Insetion | Deletion |
| :---: | :---: | :---: |
|  O(n) | O(1) | O(1) |

#### 공간 복잡도

O(n)