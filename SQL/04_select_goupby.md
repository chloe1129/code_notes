### GROUP BY

- 테이블의 레코드를 grouping하기 위해 사용
- 해당 절은 각각의 그룹에 대해 하나의 행을 만드는데 이 과정을 `aggregation`이라 부른다.
- GRUOP BY는 주로 aggregate function(COUNT,MAX,MIN,SUM,AVG)와 함께 쓰인다.
- 1개 이상의 column에 대해 grouping할 수 있다.
- SELECT 절에는 GROUP BY에 쓰인 column만 사용가능하다.

##### Person table

| id  |     name     | age |  money  | gender |  city  |
| :-: | :----------: | :-: | :-----: | :----: | :----: |
|  1  | Junkyu Park  | 27  |  50000  |   0    | Ulsan  |
|  2  | Sangheon Lee | 27  | 3000000 |   0    | Ansan  |
|  3  | Taesung Kim  | 27  |  40000  |   0    | Daegu  |
|  4  | Dohyung Kim  | 22  |  55000  |   0    | Sokcho |
|  5  | Sangwook Nam | 27  |  40000  |   0    | Seoul  |
|  6  | Nayoung Kim  | 25  |  60000  |   0    | Seoul  |
|  7  |  Jaeik Lee   | 27  |  5000   |   0    | Seoul  |

###### `city` column을 그룹핑 해서 city가 같은 데이터들을 하나로 묶어버린다.

```
SELECT Person.city from Person
GROUP BY Person.city;


GROUP BY에 명시되어있지 않은 column을 추가하면 에러가 발생한다.
SELECT Person.city, Person.name from Person
GROUP BY Person.city;
```

```
같은 도시에 살고있는 사람들을 그룹핑한 후 그 사람들이 가진 돈의 총합을 구한다.
SELECT Person.city, SUM(Person.money) from Person
GROUP BY Person.city;
```

```
각 도시에서 가장 돈이 많은 사람을 구하고 싶다.
SELECT Person.city, MAX(Person.money) from Person
GROUP BY Person.city;
```

```
ORDER BY를 사용하면, 오름차순(ASC) 또는 내림차순(DESC)으로 정렬할 수 있다.

같은 도시에 사는 사람 수를 카운트하고 이를 city의 내림차순으로 정렬한다.
SELCET Person.city, COUNT(*) from Person
GROUP BY Person.city
ORDER BY Person.city DECS;
```

```
사람들이 살고 있는 도시와, 그 도시에 살고 있는 사람들의 수를 출력하는데
이때 전체 데이터에서 그 도시에 살고 있는 사람의 수가 4명 이상인 도시와 그 사람수를 출력한다.

SELECT Person.city, COUNT(*) from Person
GROUP BY Person.city
HAVING COUNT(*) >= 4;


사람이 1명 이상 살고있는 도시에 대해 출력할 때 사람이 많이 사는 순서(내림차순)으로 출력한다.
SELECT Person.city, COUNT(*) from Person
GROUP BY Person.city
HAVING COUNT(*) >= 1
ORDER BY COUNT(*) DESC;
```

```
GROUP BY된 데이터명 중, S로 시작하는 도시와 그 도시에 사는 사람 수를 출력한다.
SELECT Person.city, COUNT(*) from Person
GROUP BY Person.city
HAVING Person.city LIKE 'S%';

위의 조건을 WHERE로 바꿀 수 있다.
SELECT Person.city, COUNT(*) from Person
WHERE Person.city LIKE 'S%'
GROUP BY Person.city;
```

```
GROUP BY에 두개 이상의 column을 넣을 수도 있다.

각 도시와 성별을 그룹으로 묶고, 각 도시별 남성, 여성중 돈이 가장 많은 사람이 얼마나 돈이 있는지 출력한다.
SELECT Person.city, Person.gender, MAX(Person.money) from Person
GROUP BY Person.city, Person.gender;

```
