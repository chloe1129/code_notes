## UNION

- 2개 이상 테이블에 존재하는 같은 성격의 값을 하나의 쿼리로 추출하느 ㄴ것
- 대응하는 칼럼의 이름이 다르다면 통일해주는 것이 좋다

table1
| id | asia |
| :-: | :----: |
| 1 | '한국' |
| 2 | '일본' |
| 3 | '중국' |

table2
| id | country |
| :-: | :------: |
| 1 | '미국' |
| 2 | '영국' |
| 3 | '독일' |
| 4 | '스페인' |
| 5 | '한국' |

> 중복되지 않은 값만 추출하는 법, UNION or UNION DISTINCT

```
SELECT asia AS 'country' FROM table1
UNION
SELECT country FROM table2
```

| country  |
| :------: |
|  '한국'  |
|  '일본'  |
|  '중국'  |
|  '미국'  |
|  '영국'  |
|  '독일'  |
| '스페인' |

> 중복을 허용하고 모든 값 추출하는 법, UNION ALL

```
SELECT asia AS 'country' FROM table1
UNION ALL
SELECT country FROM table2
```

| country  |
| :------: |
|  '한국'  |
|  '일본'  |
|  '중국'  |
|  '미국'  |
|  '영국'  |
|  '독일'  |
| '스페인' |
|  '한국'  |
