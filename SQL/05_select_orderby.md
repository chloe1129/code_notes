### OERDER BY

- 데이터를 정렬
- 기본적으로 오름차순(ASC)

###### Person table

| id  |     name     | age |  money  | gender |  city  |
| :-: | :----------: | :-: | :-----: | :----: | :----: |
|  1  | Junkyu Park  | 27  |  50000  |   0    | Ulsan  |
|  2  | Sangheon Lee | 27  | 3000000 |   0    | Ansan  |
|  3  | Taesung Kim  | 27  |  40000  |   0    | Daegu  |
|  4  | Dohyung Kim  | 22  |  5000   |   0    | Sokcho |
|  5  | Sangwook Nam | 27  |  40000  |   0    | Seoul  |
|  6  | Nayoung Kim  | 25  |  60000  |   0    | Seoul  |
|  7  |  Jaeik Lee   | 27  |  5000   |   0    | Seoul  |

```
모든 데이터를 조회할 때, id를 오름차순으로 조회한다.

SELECT * FROM Person
ORDER BY id ASC;


id를 내림차순으로 조회한다.

SELECT * FROM Person
ORDER BY id DESC;
```

```
정렬 기준을 여러개 하고 싶을 때, 컴마로 원하는 만큼 이어붙여준다.
맨 앞의 값이 같을 경우 뒤의 조건으로 정렬 기준 판별

SELECT Person.city, Person.id From Person
ORDER By Person.money DESC, Person.id;
```

```
ORDER BY뒤에 컬럼명 대신 숫자를 쓸 수 있다.
아래의 두 쿼리는 같은 결과를 나타낸다.

SELECT Person.city, Person.id From Person
ORDER By Person.money DESC, Person.id;

SELECT Person.city, Person.id From Person
ORDER By 4y DESC, 1;
```
