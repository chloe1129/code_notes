### 표준 입출력 방식 사용하기!

> 임의의 정수의 개수 한 줄에 입력받을 때

```
data = list(map(int, sys.stdin.readline().split()))
```

> 임의의 개수의 정수를 n줄 입력받아 2차원 리스트에 저장하기

```
data =[]
for i in range(n):
    data.append(list(map(int, sys.stdin.readline().split())))

```

> 문자열 n줄 입력받아 리스트에 저장

```
data = [sys.stdin.readline().strip() for i in range(n)]
```
