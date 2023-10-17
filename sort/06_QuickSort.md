### Quick Sort

- Partitioning, 파티셔닝을 이용한 알고리즘
- pivot 숫자를 기준으로 pivot 숫자만 정렬, 남은 왼쪽과 오른쪽의 배열을 각각 recursive하게 다시 sort
- O(n\*logn)의 평균 시간 복잡도를 갖고 있다.
- Stable하지 않은 정렬 방법

```
from typing import List
import random

def quickSort(nums:List[int], beginIdx:int, lastIdx:int)->List[int]:
  length = lastIdx-beginIdx+1
  if length <= 1:
    return nums

  pivotIdx = random.randrange(beginIdx,lastIdx+1)

  # pivot 숫자를 array의 맨 끝 숫자와 swap
  nums[pivotIdx],nums[lastIdx] = nums[lastIdx],nums[pivotIdx]

  leftIdx = beginIdx
  rightIdx = lastIdx-1
  pivot = nums[lastIdx]

  while leftIdx <= rightIdx:
    if nums[leftIdx] <= pivot:
      leftIdx += 1
      continue

    if pivot < nums[rightIdx]:
      rightIdx -= 1
      continue

    # pivot이 왼쪽 포인터보다 작고 오른쪽 포인터보다 크면, 두 값을 swap
    if pivot < nums[leftIdx] and nums[rightIdx] <= pivot:
      nums[leftIdx], nums[rightIdx] = nums[rightIdx], nums[leftIdx]
      continue

  # pivot 숫자는 배열의 정렬된 위치를 찾았으므로 찾은 위치로 pivot을 swap
  nums[leftIdx],nums[lastIdx] = nums[lastIdx],nums[leftIdx]

  # 남은 왼쪽, 오른 쪽 배열을 다시 quickSort 해준다.
  quickSort(nums=nums, beginIdx=leftIdx+1,lastIdx = lastIdx)
  quickSort(nums=nums, beginIdx=beginIdx, lastIdx = leftIdx-1)

  return nums

nums = [5,7,9,3,1,5,5,2,4]
quickSort(nums=nums,beginIdx=0,lastIdx=len(nums)-1)
print(nums)
```
