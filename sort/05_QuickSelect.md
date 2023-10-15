### Quick Select

- 정렬되지 않은 배열에서 n번째로 큰 or 작은 원소를 찾는 법
- Partitioning, 파티셔닝을 이용한 알고리즘
- O(n)의 시간 복잡도를 갖고있다.

> 2번째로 큰 수를 찾아라

[3 5 9 1 2 4 7]

기준 숫자, pivot을 하나 랜덤하게, 아무거나 정한다.  
기준 숫자를 기준으로 왼쪽에는 작은 숫자, 오른쪽에는 큰 숫자를 모아둔다

pivot = 4  
4 보다 작은 숫자들 < pivot = 4 < 4 보다 큰 숫자들

[3 5 9 1 2 **4** **7**] # **4**를 맨 끝 숫자와 바꿔준다.

[__3__ 5 9 1 2 __7__ **4**] # 왼쪽 끝, 오른쪽 끝에 두개의 포인터 i, j 를 **4**와 비교한다.

[3 __5__ 9 1 2 __7__ **4**] # 3은 4보다 작으므로 포인터롤 5로 옮겨준다. 5는 4보다 크기 때문에 포인터를 멈추고 뒤에서 부터 시작하는 포인터로 옮긴다.

[3 __5__ 9 1 __2__ 7 **4**] # 7은 4보다 크기 때문에 포인터를 2로 옮겨준다. 2는 4보다 작기 때문에 포인터를 멈춘다.

[3 __2__ 9 1 __5__ 7 **4**] # 더 이상 움직일 수 없기 때문에 5와 2를 swap 해준 후 다시 움직인다.

[3 2 __9__ __1__ 5 7 **4**] # 2 < 4 -> 포인터 9로 옮긴다. 9 > 4 이기 때문에 멈춘다. 1 < 4 이므로 역시 멈춘 후 swap.

[3 2 __1__ __9__ 5 7 **4**] # swap 후, 1 < 4 -> 포인터를 9로, 9 > 4 이므로 포인터를 1로 이동한다.
앞에서부터 시작한 포인터와 뒤에서부터 시작한 포인터가 바꼈다. 뒤에서부터 시작한 포인터의 위치와 4를 swap 한다.

[3 2 1 **4** 5 7 9] # 순서는 모르지만, 왼쪽엔 4보다 작은 수, 오른쪽엔 4보다 큰 수

-> 2번째로 큰 수는 4 뒤에 위치할것, [5, 7, 9] 에서 다시 `Quick Select` 진행한다.

[__5__ __9__ **7**] # 7을 랜덤 pivot으로 선택한다. 5와 9의 자리에 포인터를 다시 설정한다.

-> 5 < 7 이므로 포인터 이동, 9 > 7 이므로 멈춘다. 뒤로 가서 9 > 7 이므로 포인터를 이동하고 5 < 7 이므로 멈춘다. 두 포인터를 이동할 수 없으므로 뒤쪽 포인터의 위치와 pivot인 7을 swap 한다.

[5 7 9] # 7의 왼쪽에는 작은 숫자, 오른쪽에는 큰 숫자로 정렬되고 7의 인덱스를 알 수 있다.

[3 2 1 4 5 7 9] # 4의 오른쪽에서 다시 `Quick Select`를 진행해서 뒤에서 두번째로 큰 인덱스를 알았다.

---

> 주어진 array에서 k번째로 큰 수를 찾아라

```
from typing import List
import random

def quickSelect(nums:List[int],k:int) -> int:
  length = len(nums)

  # array의 길이가 1이라면 그대로 return
  if length == 1:
    return nums[0]

  # 랜덤으로 pivot 숫자 설정
  pivotIdx = random.randrange(length)

  # pivot이 들어갈 맨 끝 인덱스
  lastIdx = length-1

  # pivot 숫자를 array의 맨 끝 숫자와 swap
  nums[pivotIdx],nums[lastIdx] = nums[lastIdx],nums[pivotIdx]


  # 맨 앞, 맨 뒤 포인터 선언
  leftIdx = 0
  rightIdx = length-2
  pivot = nums[-1]

  # 왼쪽 포인터가 오른쪽에 가지 않을때 까지
  while leftIdx <= rightIdx:

    # 왼쪽 포인터의 값이 pivot보다 작으면 포인터 증가
    if nums[leftIdx] <= pivot:
      leftIdx += 1
      continue

    # 오른쪽 포인터의 값이 pivot보다 크면 포인터 감소
    if pivot < nums[rightIdx]:
      rightIdx -= 1
      continue

    # pivot이 왼쪽 포인터보다 작고 오른쪽 포인터보다 크면, 두 값을 swap
    if pivot < nums[leftIdx] and nums[rightIdx] <= pivot:
      nums[leftIdx], nums[rightIdx] = nums[rightIdx], nums[leftIdx]
      continue

  # pivot 숫자는 배열의 정렬된 위치를 찾았으므로 찾은 위치로 pivot을 swap
  nums[leftIdx],nums[lastIdx] = nums[lastIdx],nums[leftIdx]

  # leftIdx가 가리키는 값은 이제 정렬된 위치에 있는 pivot 값, 해당 인덱스가 찾으려는 k값인지?
  if leftIdx == length - k:
    return nums[leftIdx] # 맞으면 해당 값을 리턴

  elif leftIdx < length-k: # 정렬된 위치가 찾아야할 값보다 작으면 pivot의 오른쪽 배열로 다시 진행
    return quickSelect(nums=nums[leftIdx+1:],k=k)

  elif length-k < leftIdx: # 정렬된 위치가 찾아야할 값보다 크면 pivot의 왼쪽 배열로 다시 진행
    return quickSelect(nums=nums[:leftIdx],k=k-(length-leftIdx))


quickSelect(nums=[5,7,9,3,1,2,4],k=2)
```
