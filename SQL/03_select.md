### SELECT (조회)

테이블에서 데이터를 조회

```
SELECT 칼럼명1, 칼럼명2
    [FROM 테이블명 ]
    [GROUP BY 칼럼명]
    [ORDER BY 칼럼명 [ASC | DESC]]
    [LIMIT offset, 조회 할 행의 수]

```

```
SELECT * FROM student; # student에 있는 모든 칼럼 조회

SELECT name, birthday FROM student; # student에 있는 name과 birthday 칼럼을 조회

SELECT * FROM student WHERE id=3; # student에 id=3인 칼럼만 조회

SELECT * FROM student WHERE sex='남자' AND address='서울'; # student에 sex='남자' 와 address='서울'인 칼럼만 조회

SELECT * FROM student LIMIT 1; # student에 있는 칼럼 중 위에서부터 1개의 자료만 보도록 제한

SELECT * FROM student LIMIT 1,1; # student에 있는 칼럼 중 인덱스 1부터 1개의 자료만 보도록 제한
SELECT * FROM student LIMIT 2,1; # student에 있는 칼럼 중 인덱스 2부터 1개의 자료만 보도록 제한

SELECT * FROM student WHERE sex='남자' LIMIT 2; # student에 있는 칼럼 중 sex='남자' 중 2개의 자료만 보도록 제한
```
