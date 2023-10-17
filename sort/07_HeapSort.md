### Heap Sort

- Heap 구조를 이용한 알고리즘
- Max heap: 부모노드가 모든 자식 노드보다 항상 값이 클 때
- Min heap: 부모노드가 모든 자식 노드보다 항상 값일 작을 때
- Heapify: 배열이나 이진트리를 힙 구조로 재배열하는 것

> 파이썬에서의 Heap, heapq 라이브러리 이용

- `import heapq` 로 사용할 수 있다.
- `heapq.heappush(heap, item,)` : item을 heap에 추가
- `heap.heappop(heap)` : heap에서 가장 작은 원소를 pop & 리턴, 비어있는 경우 IndexERROR
- `heapq.heapify(x)` : 리스트 x를 즉각적으로 heapq로 변환

```
from typing import List
import heapq


def heapSort(nums:List[int])->List[int]:
  # 파이썬의 heapq는 max힙이 아니라 min힙이다. 그래서 -1을 곱해 가장 큰 수에 마이너스가 붙어 가장 작은 수가 되게끔한다.
  nums = [-1*n for n in nums]
  heapq.heapify(nums)

  sorted = [0] * len(nums)

  for i in range(len(nums)-1,-1,-1):
    largest = -1 * heapq.heappop(nums)
    sorted[i] = largest
  return sorted

print(heapSort(nums=[3, 5, 7, 9, 4, 2]))

```
