### WHERE

- 테이블에서 특정 조건에 부합하는 데이터만 조회하고 싶을 때 사용한다.

###### Person table

| id  |     name     | age | money  | gender |  city  |
| :-: | :----------: | :-: | :----: | :----: | :----: |
|  1  | Junkyu Park  | 27  | 50000  |   0    | Ulsan  |
|  2  | Sangheon Lee | 27  | 300000 |   0    | Ansan  |
|  3  | Taesung Kim  | 27  | 40000  |   0    | Daegu  |
|  4  | Dohyung Kim  | 22  |  5000  |   0    | Sokcho |
|  5  | Sangwook Nam | 27  | 40000  |   0    | Seoul  |
|  6  | Nayoung Kim  | 25  | 60000  |   0    | Seoul  |
|  7  |  Jaeik Lee   | 27  |  5000  |   0    | Seoul  |

```
city가 Seoul인 데이터만 조회한다.

SELECT * FROM Person
WHERE Person.city = 'Seoul';


money가  50000이상인 데이터만 조회한다.

SELECT * FROM Person
WHERE Person.money >= 50000;
```

#### 논리 연산자 `(and/or)`

```
city가 seoul이
면서 money가 50000 이상인 데이터를 조회한다.

SELECT * FROM Person
WHERE Person.city = 'seoul' and Person.money >= 50000;
```

#### BETWEEN A and B

```
money가 50000 이상 500000 이하인 데이터를 조회한다.

SELECT * FROM Person
WHERE Person.money >= 50000
and Person.money <= 500000;


위의 쿼리와 같은 결과를 보인다.

SELECT * FROM Person
WHERE Person.money BETWEEN 50000 and 500000;
```

#### IN

```
money가 40000, 50000인 데이터를 조회한다.

SELECT * FROM Person
WHERE money IN(40000,50000);
```
