## Hash Table(해시 테이블, 해시 맵)

> 키(key)를 값(value)에 매핑할 수 있는 구조인 연관 배열을 구현하는 자료구조

해쉬 함수를(Hash Function) 사용해 원하는 값을 담을 수 있는 버킷(Bucket) 또는 슬롯(Slot) 배열의 인덱스(index)를 계산한다.

![hash-table](https://github.com/kwhong95/js_study/assets/70752848/508d99e5-f53e-4f7a-a560-2aa442094c03)

---

대부분의 해시 테이블은 불완전한 해시 함수를 사용하기 때문에 해시 함수를 통해 두 개 이상의 키에 대해 동일한 인덱스를 생성하는 *해시 충돌* 이 발생할 수 있다.

---

### 분리 연결법(Separate Chaining)

> 각 해시 테이블의 버킷(bucket)에 연결 리스트(Linked List)를 사용하여 충돌된 데이터를 저장하는 것입니다. 각 버킷은 연결 리스트의 헤드를 가리키며, 충돌이 발생했을 때 새로운 데이터를 해당 버킷의 연결 리스트에 추가합니다.

![collision-resolution](https://github.com/kwhong95/js_study/assets/70752848/20599db1-701c-4c37-9340-f3c82ceca400)


#### 분리연결법 요약 절차

1. 해시 함수를 사용하여 각 키를 해당 버킷(index)으로 매핑합니다.
2. 충돌이 발생한 경우, 해당 버킷에 연결 리스트를 이용하여 데이터를 추가합니다.
3. 추가할 때에는 해당 버킷의 연결 리스트를 탐색하여 중복된 키가 있는지 확인하고, 없다면 새로운 노드를 연결 리스트에 추가합니다.
4. 검색이나 삭제를 할 때에도 해당 버킷의 연결 리스트를 순회하여 작업을 수행합니다.


### 활용 사례 

> 사용자 정보를 저장하고 검색하는 용도로 해시 테이블을 활용 

사용자의 아이디를 키로 사용하여 해당 사용자의 정보를 효율적으로 관리하고, 빠르게 검색하거나 업데이트할 수 있습니다.

### 활용 사례 코드

```ts
// Node 클래스: 연결 리스트의 노드를 나타내는 클래스
class UserNode {
  public key: string;
  public user: IUser;
  public next: UserNode | null;

  constructor(key: string, user: IUser) {
    this.key = key;
    this.user = user;
    this.next = null;
  }
}

// HashTable 클래스: 분리 연결법을 사용하는 Hash Table 클래스
class HashTableSeparateChaining {
  private table: (UserNode | null)[];

  constructor(size: number) {
    this.table = new Array(size).fill(null);
  }

  // 해시 함수: 간단히 key의 길이를 해시 테이블의 크기로 나눈 나머지를 해시 값으로 사용
  private hash(key: string): number {
    return key.length % this.table.length;
  }

  // 사용자 정보를 추가하는 메서드
  public insertUser(key: string, user: IUser) {
    const index = this.hash(key);
    const newNode = new UserNode(key, user);

    if (!this.table[index]) {
      this.table[index] = newNode;
    } else {
      let current = this.table[index];

      while (current?.next) {
        current = current.next;
      }
      current!.next = newNode;
    }
  }

  // 사용자 정보를 검색하는 메서드
  public findUser(key: string): IUser | null {
    const index = this.hash(key);
    let current = this.table[index];

    while (current) {
      if (current.key === key) {
        return current.user;
      }
      current = current.next;
    }

    return null;
  }
}

// 사용자 정보를 담는 인터페이스
interface IUser {
  name: string;
  age: number;
  email: string;
}

// 사용자 정보를 해시 테이블(분리 연결법)에 저장하는 예시
const userTableSeparateChaining = new HashTableSeparateChaining(10);

// 사용자 정보 추가
userTableSeparateChaining.insertUser("1234", {
  name: "Alice",
  age: 30,
  email: "alice@example.com",
});
userTableSeparateChaining.insertUser("5678", {
  name: "Bob",
  age: 25,
  email: "bob@example.com",
});

// 사용자 정보 검색
const user1 = userTableSeparateChaining.findUser("1234"); // Alice
const user2 = userTableSeparateChaining.findUser("9999"); // 사용자를 찾을 수 없음 (= null)
```
