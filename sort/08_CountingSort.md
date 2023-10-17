### Counting Sort

- 계수 정렬
- O(n)의 시간복잡도
- 배열의 길이는 (가장 큰 수 - 가장 작은 수 + 1)
- 원소의 크기가 한정된 경우에 사용하면 유리하다.
- stable한 알고리즘이다.

> Array 정렬

[ 3 0 5 1 0 5 ] # 각 원소들의 개수를 세야한다.

i 0 1 2 3 4 5
[ 2 1 0 1 0 2 ] # count array  
[ 2 3 3 4 4 6 ] # 누적합  
[ 1 2 2 3 3 5 ] # counting으로 개수를 세었기 때문에 누적합에서 -1을 해준다

주어진 array의 뒤에서부터 탐색한다.  
5 -> 5번째 인덱스의 값 5 , 카운트 배열의 해당 인덱스의 값에 -1을 해준다.  
[ _ _ _ _ _ 5 ]

[ 1 2 2 3 3 4 ]  
0 -> 0번째 인덱스의 값 1  
[ _ 0 _ _ _ 5 ]

[ 0 2 2 3 3 4 ]  
1 -> 1번째 인덱스 2  
[ _ 0 1 _ _ 5 ]

[ 0 1 2 3 3 4 ]  
5->5번째 인덱스 값 4  
[ _ 0 1 _ 5 5 ]

[ 0 1 2 3 3 3 ]  
0->0번째 인덱스 값 0  
[ 0 0 1 _ 5 5 ]

[ 0 1 2 3 3 3 ]  
3->3번째 인덱스 값 3  
[ 0 0 1 3 5 5 ]

```
from typing import List

def countingSort(nums:List[int])->List[int]:
  length = len(nums)
  min_num = min(nums)  #offset
  max_num = max(nums)

  range = max_num - min_num + 1
  counts = [0]*range

  for num in nums:
    count_idx = num - min_num
    counts[count_idx] += 1

  acc_counts = []
  acc_count = 0
  for count in counts:
    acc_count += count
    acc_counts.append(acc_count)

  end_locs = [ c-1 for c in acc_counts]

  sorted = [0] * length
  for num in reversed(nums):
    count_idx = num - min_num
    end_loc = end_locs[count_idx]
    sorted[end_loc] = num
    end_locs[count_idx] -= 1

  return sorted

print(countingSort(nums=[3,4,0,1,2]))
print(countingSort(nums=[3,0,5,1,0,5]))
```
