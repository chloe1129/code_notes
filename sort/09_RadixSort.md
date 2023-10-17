### Radix Sort

- counting sort를 활용한 알고리즘이다.
- 숫자 자체가 아닌 자리수를 활용해서 정렬한다.
- stable sort 원칙을 지킨다.
- 시간 복잡도 O(n+k) \* w
- k: 기준으로 가진 진수, 아래에서는 10진수이므로 10 , w: 최대 자리수

> Array 정렬

[ 391 582 50 924 134 8 192 ]

1의 자리를 기준으로 정렬한다.  
[ 50 391 582 192 924 134 8 ]

10의 자리 기준으로 다시 정렬한다.  
[ 8 924 134 50 582 391 192 ]

200의 자리 기준으로 다시 정렬한다.  
[ 8 50 134 192 392 582 924 ]

```
from typing import List
import math

def countingSortByDigit(nums:List[int],digit:int)->List[int]:
  counts = [0]*10
  for num in nums:
    count_idx = num//pow(10,digit)%10
    counts[count_idx] += 1

  acc_counts = []
  acc_count = 0
  for count in counts:
    acc_count += count
    acc_counts.append(acc_count)
  end_locs = [ c-1 for c in acc_counts]

  sorted = [0] * len(nums)
  for num in reversed(nums):
    count_idx = num//pow(10,digit)%10
    end_loc = end_locs[count_idx]
    sorted[end_loc] = num
    end_locs[count_idx] -= 1

  return sorted


def radixSort(nums:List[int])->List[int]:
  largest_num = max(nums)
  digits = int(math.log10(largest_num))+1
  sorted = nums
  for digit in range(digits):
    sorted = countingSortByDigit(nums=sorted,digit=digit)
  return sorted

print(radixSort(nums=[391,582,50,924,8,192]))
```
