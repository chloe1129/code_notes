## JOIN

### JOIN을 크게 구별하는 두가지 방법!

> `JOIN` 조건으로 사용되는 연산자에 따른 분류

- `EQUI JOIN` : 두 테이블 간의 칼럼 값들이 서로 일치하는 경우, `JOIN` 조건으로 '=' 연산자 사용

```
아래 두가지 모두 EQUI JOIN

SELECT 칼럼_이름 FROM 테이블1, 테이블2
WHERE 테이블1.칼럼_이름 = 테이블2.칼럼_이름;

SELECT * FROM 테이블1 JOIN 테이블2 [ON 조인 조건에 따라]
```

- `NON EQUI JOIN` : 두 테이블 간의 값들이 일치하지 않는 경우, `JOIN` 조건으로 `BETWEEN`, `AND` 등의 범위 비교 연산자를 사용

> `FROM` 절의 `JOIN` 형태에 따른 분류

- `INNER JOIN` : JOIN 조건에서 값이 일치하는 행만 변환
- `OUTER JOIN` : JOIN 조건에서 한쪽 값이 없더라도 행을 반환

> 기본적인 `JOIN` 문법

```
SELECT 테이블이름.칼럼_이름
FROM 테이블이름1 {join_type} JOIN 테이블이름2 ON {join_condition}
```

    - `join_type` : 조인의 종류 outer, inner, etc..
    - `join_condition` : 조인의 조건

---

### Inner Join

- 가장 많이 사용되는 join 구문 중 하나
- condition에 따라 2개의 테이블의 컬럼을 합쳐 새로운 테이블을 생성한다.
- inner join을 한 결과에 join 조건문을 충족시키는 데이터를 반환

<center>
<img src= "../img/inner_join.jpeg" width="400px"></img>
</center>

Users
| id | name | age | gender |
| :-: | :----------: | :-: | :----: |
| 1 | Junkyu Park | 27 | 0 |
| 2 | Sangheon Lee | 27 | 0 |
| 3 | Taesung Kim | 27 | 0 |

Wealth
| user_id | money | city |
| :-----: | :---: | :---: |
| 1 | 50000 | Ulsan |
| 3 | 40000 | Daegu |

> 위와 같은 데이터가 있을 때, Users 테이블과 Wealth 테이블에서 user_id가 일치하는 row들에 대해 Inner Join을 수행한다.

```
SELECT Users.*, Wealth.*
FROM Users
INNER JOIN Wealth
ON Users.id = Wealth.user_id;
```

Inner Join
| id | name | age | gender |user_id | money | city |
| :-: | :----------: | :-: | :----: | :-----: | :---: | :---: |
| 1 | Junkyu Park | 27 | 0 | 1 | 50000 | Ulsan |
| 3 | Taesung Kim | 27 | 0 | 3 | 40000 | Daegu |
