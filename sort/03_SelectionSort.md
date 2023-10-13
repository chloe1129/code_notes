### Selction Sort

- 동일한 값을 가지는 원소들의 본래 순서가 유지되지 않는, Stable 하지 않은 정렬이다.

> 배열을 오름차순으로 정렬

[**3** 5 9 <U>1</U> 7] 3을 기준으로 5부터 포인터를 설정해 하나씩 3과 비교, 작은 값을 만나면 swap  
[1 **5** 9 3 7] 5을 기준으로 9부터 포인터를 설정해 하나씩 5과 비교, 작은 값을 만나면 swap  
[1 3 **9** 5 7] 9을 기준으로 5부터 포인터를 설정해 하나씩 9과 비교, 작은 값을 만나면 swap  
...  
[1 3 5 7 9]  

---  
  

> 평균 O(n\*\*2)의 시간복잡도

```
def sort(nums: List[int]) -> List[int]:
  for idx in range(0,len(nums)):
    minNum = nums[idx]
    minIdx = idx
    for i in range(idx,len(nums)):
      if nums[i] < minNum:
        minNum = nums[i]
        minIdx = i
    nums[idx],nums[minIdx] = nums[minIdx],nums[idx] #swap
  return nums
```
