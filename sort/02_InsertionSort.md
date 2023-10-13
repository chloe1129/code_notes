### Insertion Sort

- 패스가 거듭될 수록 탐색 범위가 늘어난다.
- 바깥 루프는 순방향, 내부 루프는 역방향 진행
- 동일한 값을 가지는 원소들의 본래 순서가 유지된다. -> 안정정렬(Stable Sort)
- 별도의 추가 공간 없이 위치만 변경, 공간 복잡도 O(1)

> 배열을 오름차순으로 정렬

[9 **3** 5 7 1] 9는 정렬이 되어있다고 생각, 3의 위치를 찾아준다.  
[3 9 **5** 7 1] 5을 잡아서 오름차순이 되는 위치에 삽입  
[3 5 9 **7** 1] 7을 잡아서 오름차순이 되는 위치에 삽입  
[3 5 7 9 **1**] 1을 잡아서 오름차순이 되는 위치에 삽입  
[1 3 5 7 9]  

---

> 평균 O(n\*\*2)의 시간복잡도

```
def insertion(nums):
    for pidx in range(1,len(nums)):
        tmp = nums[pidx]
        idx = pidx -1
        while 0<= idx and tmp < nums[idx]:
            nums[idx+1] = nums[idx]
            idx-=1
        nums[idx+1] = tmp
    return nums
```
