### Merge Sort

- 분할 정복(Devide and Conquer) 기법과 재귀 알고리즘을 이용한 정렬 알고리즘이다.
- 새로운 배열에 저장하므로 공간 복잡도는 O(n)
  

> 배열을 오름차순으로 정렬
  
[7 3 1 5 6 4 2]  
  
devide  
: 재귀의 형식을 이용해 가장 작은 길이가 될 때까지 분할한다.  
-> 7 3 1 | 5 6 4 2  
-> 7 | 3 1 | 5 6 | 4 2  
-> 7 | 3 | 1 | 5 | 6 | 4 | 2  
  
conquer  
: 비교할 2개의 배열에 각각 포인터를 설정한다. 포인터가 가리키는 원소의 크기를 비교해 결과에 넣어주고 포인터를 움직인다.  
-> 7 | 1 3 | 5 6 | 2 4  
-> 1 3 7 | 2 4 5 6  
-> 1 2 3 4 5 6 7  

---  

  
> 평균 O(n\*logn)의 시간복잡도

    배열의 분할에 log_2n,
    원소의 개수마다 분리와 병합이 나타나므로 n번의 연산

```
def mergeSort(nums:List[int]) -> List[int]:

  # split
  length = len(nums)
  if length == 1:
    return nums

  mid = length//2

  left_nums = nums[:mid]
  right_nums = nums[mid:]

  # recursive
  sorted_left = mergeSort(nums=left_nums)
  sorted_right = mergeSort(nums=right_nums)

  sorted_nums = []
  idx_l = 0
  idx_r = 0
  while idx_l<len(sorted_left) or idx_r < len(sorted_right):
    if idx_l == len(sorted_left):
      sorted_nums.append(sorted_right[idx_r])
      idx_r += 1
      continue

    if idx_r == len(sorted_right):
      sorted_nums.append(sorted_left[idx_l])
      idx_l += 1
      continue

    if sorted_right[idx_r] <= sorted_left[idx_l]:
      sorted_nums.append(sorted_right[idx_r])
      idx_r += 1
    else:
      sorted_nums.append(sorted_left[idx_l])
      idx_l += 1

  return sorted_nums

```
