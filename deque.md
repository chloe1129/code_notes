# deque (덱)

> 단방향 흐름이던 기존 Queue와 달리 양방향에서 삽입,삭제를 할 수 있는 자료구조
> queue.Queue() 가 멀티스레딩을 위한 큐여서 시간 효율이 좋지 않음
> 보통 Python으로 큐를 사용해야 할 경우 deque를 대신 사용

1. collections 모듈 및 deque import

```
from collections import deque
```

2. deque 생성

```
dq = deque()

# deque([])
```

3. append() : deque 뒤(오른쪽)에 값 추가

```
dq.append(5)
dq.append(6)

# deque([5, 6])
```

4. appendleft() : deque 앞(왼쪽)에 값 추가

```
dq.appendleft(4)
dq.appendleft(3)

# deque([3, 4, 5, 6])
```

5. extend() : deque 뒤(오른쪽)에 iterable 객체를 순환하며 값들을 차례로 추가

```
dq.extend([7, 8, 9])

# deque([3, 4, 5, 6, 7, 8, 9])
```

6. extendleft() : deque 앞(왼쪽)에 iterable 객체를 순환하며 값들을 차례로 추가

```
dq.extendleft([2, 1, 0])

# deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

7. remove() : deque 안의 특정 값 삭제

```
dq.remove(7)
dq.remove(8)
dq.remove(9)

# deque([0, 1, 2, 3, 4, 5])
```

8. pop() : deque 뒤(오른쪽)의 값 삭제 후 반환

```
popValue = dq.pop()
print(popValue)  # print결과 : 6

# deque([0, 1, 2, 3, 4, 5])
```

9. popleft() : deque 앞(왼쪽)의 값 삭제 후 반환

```
popValue = dq.popleft()
print(popValue)  # print결과 : 0

# deque([1, 2, 3, 4, 5])
```

10. rotate() : deque 안의 값들 회전

```
print(dq)  # deque([1, 2, 3, 4, 5])

dq.rotate(1)
print(dq)  # deque([5, 1, 2, 3, 4])

dq.rotate(-1)
print(dq)  # deque([1, 2, 3, 4, 5])

dq.rotate(-1)
print(dq)  # deque([2, 3, 4, 5, 1])
```
