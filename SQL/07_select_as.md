### AS

- SELECT 문을 사용할 때, 결과로 나오는 column에 as 로 별칭을 줄 수 있다.

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
SELECT * FROM Person
WHERE Person.city = 'Ulsan';
```

| id  |    name     | age | money | gender | city  |
| :-: | :---------: | :-: | :---: | :----: | :---: |
|  1  | Junkyu Park | 27  | 50000 |   0    | Ulsan |

|  
|  
v  

```
SELECT city AS 도시, name AS 이름 FROM Person
WHERE Person.city = 'Ulsan';
```

|    이름     | 도시  |
| :---------: | :---: |
| Junkyu Park | Ulsan |
