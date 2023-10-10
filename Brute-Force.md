# Brute-Force Algorithm

> 완전 탐색 알고리즘 (무식하게 풀기)

모든 경우의 수를 다 탐색해보는 알고리즘

정확도는 100% 보장되지만 속도는 최악, 따라서 주어진 데이터가 매우 적을 때만 사용

주로 for문/if문, BFS/DFS (백트랙킹), 비트마스크를 활용해 구현
순열/조합을 활용해 구현하는 방법을 연습해두자

순간 순열이 뭔지 까먹은거 실화냐? 서로 다른 n개의 원소에서 r개를 중복없이 순서에 상관있게 선택 혹은 나열하는것......
조합은 순서와 상관 없게.....!!

> 재귀적으로 순열을 구현하는 방법

```
def permutation(arr, r):
    # 순열을 저장할 배열
    result = []

    # 실제 순열을 구하는 함수
    def permute(p, index):
        if len(p) == r:
        result.append(p)
            return

        for idx, data in enumerate(arr):
            if idx not in index:
				# list는 mutable이기 때문에 새로운 리스트를 넘겨준다.
            	permute(p + [data], index + [idx])

    permute([], [])

    return result

for r in permutation(['A', 'B', 'C', 'D'], 2):
    print(r)


# --- Result ---
['A', 'B']
['A', 'C']
['A', 'D']
['B', 'A']
['B', 'C']
['B', 'D']
['C', 'A']
['C', 'B']
['C', 'D']
['D', 'A']
['D', 'B']
['D', 'C']
```

> 재귀적으로 조합을 구현하는 법

```
def combination(arr, r):

    # 조합을 저장할 배열
    result = []

    # 실제 조합을 구하는 함수
    def combinate(c, index):
        if len(c) == r:
            result.append(c)
            return

        for idx, data in enumerate(arr):
            # 중복되는 조합이 생성되지 않게 마지막으로 들어온 원소의 인덱스보다
            # 새로 추가하는 원소의 인덱스가 큰 경우만 조합을 생성한다.
            if idx > index:
                combinate(c + [data], idx)

    combinate([], -1)

    return result

for r in combination(['A', 'B', 'C', 'D'], 2):
    print(r)

# --- Result ---
['A', 'B']
['A', 'C']
['A', 'D']
['B', 'C']
['B', 'D']
['C', 'D']
```
