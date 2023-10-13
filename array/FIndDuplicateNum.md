### Find duplicates

> 1부터 5까지의 숫자로 하나씩 구성된 배열에 1부터 5까지의 숫자 중 하나가 추가로 들어갔다. 추가로 들어간 숫자 하나를 찾아라

| index |  0  |  1  |  2  |  3  |  4  |  5  |
| :---: | :-: | :-: | :-: | :-: | :-: | :-: |
| value |  5  |  4  |  3  |  2  |  1  |  2  |

```
# abs() : 절대값 함수
num = [1,2,3,4,5,2]


for i in range(len(num)):
    if nums[abs(nums[i])] < 0 :
        return abs(nums[i])
    nums[abs(nums[i])] = - nums[abs(nums[i])]
```

- `i = 0` 일 때, `num[0] = 5`
- `num[5]`의 값 `2 -> -2` 로 변경
- `if num[i] < 0` 이라면, 해당 `num[i]`의 값이 중복된 것!

> 시간 복잡도 `O(n)`, 공간 복잡도 `O(1)`

---
