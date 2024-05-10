## Heap(힙)

> 아래 힙 속성을 만족하는 전문화된 트리 기반 데이터 구조

### MIN HEAP

> 최소 합에서 $P$가 $C$의 상위 노드라면 $P$의 키(값)는 $C$의 키보다 작거나 같습니다

![min-heap](https://github.com/kwhong95/js_study/assets/70752848/4e206784-7cf8-4d79-9102-200769d6c7db)

### MAX HEAP

> 최대 힙에서 $P$의 키는 $C$의 키보다 크거나 같습니다.

![max-heap](https://github.com/kwhong95/js_study/assets/70752848/a3848cad-2f70-450c-9d13-a22f6f81bb9c)

![array-representation](https://github.com/kwhong95/js_study/assets/70752848/4f1bcfde-c934-468e-9e0e-2883df4a08e8)

상위 노드가 없는 힙의 "상단"에 있는 노드를 루트 노드라고 합니다.

## 활용 사례

### 동적 메모리 할당

```ts
function createDynamicArray(size: number): number[] {
  const dynamicArray = new Array(size);
  for (let i = 0; i < size; i++) {
    dynamicArray[i] = i * 2; 
  }
  return dynamicArray;
}

// Heap Memory를 활용한 동적 배열 예시
const dynamicArraySize = 5;
const myDynamicArray = createDynamicArray(dynamicArraySize);

// 동적 배열 출력
console.log("Dynamic Array:", myDynamicArray);

// 동적 배열에서 합 구하기
const sum = myDynamicArray.reduce((acc, val) => acc + val, 0);
console.log("Sum of Dynamic Array:", sum);
```