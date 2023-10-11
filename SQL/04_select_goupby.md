### GROUP BY

- 테이블의 레코드를 grouping하기 위해 사용
- 해당 절은 각각의 그룹에 대해 하나의 행을 만드는데 이 과정을 `aggregation`이라 부른다.
- GRUOP BY는 주로 aggregate function(COUNT,MAX,MIN,SUM,AVG)와 함께 쓰인다.
- 1개 이상의 column에 대해 grouping할 수 있다.
- SELECT 절에는 GROUP BY에 쓰인 column만 사용가능하다.

###### table, sample data

| id  |     name     | age |  money  | gender |  city  |
| :-: | :----------: | :-: | :-----: | :----: | :----: |
|  1  | Junkyu Park  | 27  |  50000  |  b'0'  | Ulsan  |
|  2  | Sangheon Lee | 27  | 3000000 |  b'0'  | Ansan  |
|  3  | Taesung Kim  | 27  |  40000  |  b'0'  | Daegu  |
|  4  | Dohyung Kim  | 22  |  55000  |  b'0'  | Sokcho |
|  5  | Sangwook Nam | 27  |  40000  |  b'0'  | Seoul  |
|  6  | Nayoung Kim  | 25  |  60000  |  b'0'  | Seoul  |
|  7  |  Jaeik Lee   | 27  |  5000   |  b'0'  | Seoul  |
|  8  |  Daeho Lee   | 29  | 3400000 |  b'0'  | Seoul  |
