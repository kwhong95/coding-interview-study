## 자료구조
 
1. [Linked List(연결 리스트)](/data-structures/linkedList.md)
2. [Doubly Linked List(이중 연결 리스트)](/data-structures/doublyLinkedList.md)
3. [Queue(큐)](/data-structures/queue.md)
4. [Stack(스택)](/data-structures/stack.md)
5. [Hash Table(해시 테이블)](/data-structures/hashTable.md)
6. [Heap(힙)](/data-structures/heap.md)


### Big O 표기법

> 알고리즘의 성능을 수학적으로 표기한것(시간 / 공간복잡도)

#### 1. $O(1)$

```c
F(int[] n){
  return (n[0] === 0) ? true : false
}
```

![23](https://github.com/kwhong95/coding-interview-study/assets/70752848/966e263d-41e2-432b-8fc1-1843d8629231)

입력 데이터의 크기에 상관없이 언제나 일정한 시간이 걸리는 알고리즘을 말한다.
데이터가 증가함에 따라 성능에 변함이 없다.

#### 2. $O(n)$ 데이터와 시간이 같은 비율로 증가

```c
F(int[] n) {
  for i = 0 to n.length
  print i
}
```

![on](https://github.com/kwhong95/coding-interview-study/assets/70752848/f8243838-1b8d-4d4d-8714-c0edf25e36de)
![on(1)](https://github.com/kwhong95/coding-interview-study/assets/70752848/876d3d2c-8fbf-4606-b018-9c6c647cc661)

입력 데이터의 크기에 비례해서 처리시간이 걸리는 알고리즘을 표현할 때 사용한다.
데이터가 증가함에 따라 처리 시간도 비례해서 증가한다.

#### 3. $O(n^2)$

```c
F(int[] n) {
  for i = 0 to n.length
  for j = 0 to n.length

  print i + j
}
```

$n$ 을 순회하며 $n$으로 루프를 돌릴 때 $n$ square 가 된다.

![On2](https://github.com/kwhong95/coding-interview-study/assets/70752848/f1b2e6bd-b5b0-40b3-af1c-60271fe1283f)

$n$이 가로세로 면적만큼의 길이로 는다.
$n$이 하나 늘어날 때마다 아래한줄 오른쪽에 한줄 $n$만큼씩 이어 붙는다.
데이터가 커질수록 데이터 처리시간의 부담이 커진다.

![on2 graph](https://github.com/kwhong95/coding-interview-study/assets/70752848/9bbf8da4-6600-4488-8962-bf31fcffc09c)

#### 4. $O(nm)$

```c
F(int [] n, int[] m) {
  for i = to n.length
  for j = 0 to m.length
  print i + j
}
```

코드가 $O(n^2)$와 유사하지만, $n$을 두 번 순회하는게 아닌 $m$을 $n$ 만큼 두 번 순회하는 것을 의미한다.

![Onm](https://github.com/kwhong95/coding-interview-study/assets/70752848/e0355956-8328-48d6-aa40-11d3b756057c)

$n$ 과 $m$ 의 크기 변동이 클 수 있으므로 표기법에 다르게 표기 해줘야 한다.

![Onm(1)](https://github.com/kwhong95/coding-interview-study/assets/70752848/f3d2c5c5-567a-4bb9-ac44-8f66e957ade8)

데이터가 증가할수록 그래프가 점점 수직에 가까운 모양이 된다.

#### 5. $O(n^3)$

```c
F(int[] n) {
  for i = 0 to n.length
  for j = 0 to n.length
  for k = 0 to n.length
  print i + j + k
}
```

$n^2$ 에 $n$을 한번 더 순회한 것
  루프를 $n$을 가지고 삼중으로 돌리면 $n^3$이 된다.


$O(n)$일때는 아래와 같이 직선이고,

![on(1)](https://github.com/kwhong95/coding-interview-study/assets/70752848/876d3d2c-8fbf-4606-b018-9c6c647cc661)

$n^2$일때는 면적이였다.

![On2](https://github.com/kwhong95/coding-interview-study/assets/70752848/f1b2e6bd-b5b0-40b3-af1c-60271fe1283f)

$n^3$은 큐브 형태가 된다.

![On3](https://github.com/kwhong95/coding-interview-study/assets/70752848/8040a7a1-46b2-4606-95d7-60cb3905ff1a)

![On3 graph](https://github.com/kwhong95/coding-interview-study/assets/70752848/459ebb5a-a7df-48cf-a77d-454c296ea4da)

$n^2$과 비슷한 양상을 보이지만 데이터가 늘어날때마다 더욱 급격하게 처리 시간이 늘어난다.

#### 6. $O(2^n)$ 

피보나치 수열을 생각해보자.
  1부터 시작해 한면을 기준으로 정사각형을 만든다.

![On2](https://github.com/kwhong95/coding-interview-study/assets/70752848/b534e6f1-6212-4e8a-ac65-38a849efd6f6)

![O2n(2)](https://github.com/kwhong95/coding-interview-study/assets/70752848/370ed85f-89f5-447a-8d3f-a171649710f5)

```c
F(n, r) {
  if (n <= 0) return 0;
  else if (n == 1) return r[n] = 1
  return r[n] = F(n - 1, r) + F(n - 2, r)
}
```
(피보나치 수열을 재귀함수를 이용해서 구현한 모습)

  함수를 호출할 때마다 바로 전의 숫자랑 전전 숫자를 알아야 더할수 있으므로 해당 숫자를 알아내기 위해서
  하나뺀 숫자를 가지고 재귀호출을 하고 두개 뺀 숫자를 가지고 한번 더 호출한다.
  그걸 트리의 높이만큼 반복한다.

![O2n(3)](https://github.com/kwhong95/coding-interview-study/assets/70752848/964f7ae6-2394-4f09-85d6-f2a72726fbec)

![O2n(4)](https://github.com/kwhong95/coding-interview-study/assets/70752848/74f852e1-2ebd-4538-9f8d-d9006606fd3c)

데이터 증가에 따라 처리시간이 현저하게 증가하는 것을 볼 수 있다.

#### 7. $O(mn)$ : $m$개씩 $n$번 늘어나는 알고리즘(2대신에 $m$을 써서 표현하면 된다.)

#### 8. $O(logn)$

![Ologn](https://github.com/kwhong95/coding-interview-study/assets/70752848/3d06ef0a-c6f2-4a55-a47f-40700193d8ef)
대표적인 이진검색

정렬이 된 배열에서 6을 찾아보자.
우선 가운데 값을 찾아서 key인 6과 비교를한다.

![Ologn(1)](https://github.com/kwhong95/coding-interview-study/assets/70752848/d24f2c18-ca83-4fc0-8b8f-6ec72a2db381)

그 다음에 뒤쪽에 있는 값의 중간값과 키 값을 비교한다.

![Ologn(2)](https://github.com/kwhong95/coding-interview-study/assets/70752848/7209ec03-13fa-4cac-b89f-047c82ac6f60)

![Ologn(3)](https://github.com/kwhong95/coding-interview-study/assets/70752848/8c7030e8-db3c-4bfa-bb23-f65b517304b5)

이렇게 한번 처리가 진행될 때마다 검색해야될 데이터 양이 절반씩 줄어든다.

```c
F(k, arr, s, e) {
  if (s > e) return -1 
  m = (s + e) / 2
  if (arr[m] == k) return m
  else if (arr[m] > k) return F(k, arr, s, m-1)
  else return F(k, arr, m+1, e)
}
```

처음 호출할 때 시작부분인 s는 0, 끝지점인 m은 배열의 맨 마지막
  주어진 배열의 중간값을 찾는다.
  찾는 값이 중간값보다 작으면 중간지점 바로 전까지 array를 조정해서 다시 호출한다.
  키 값이 중간값보다 크면 중간지점 다음부터 맨 끝인 e까지 호출한다.
  이렇게 함수를 호출할때 마다 절반은 영역에서 제외시키므로 속도가 빠르다.


![Ollogn grapy](https://github.com/kwhong95/coding-interview-study/assets/70752848/6d93f750-60a5-4938-9d38-8eb34658cbf7)

$O(n)$ 보다 적은 소모값이 드는데, 데이터가 증가해도 성능에 크게 차이가 없다.


