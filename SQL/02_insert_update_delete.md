## 삽입 (INSERT)

데이터를 삽입

```
INSERT INTO table_name
VALUES (value1, value2, value3,...);

INSERT INTO table_name (column1, column2, column3,...)
VALUES (value1, value2, value3,...);
```

### 변경 (UPDATE)

데이터를 수정

```
UPDATE 테이블명 SET 컬럼1=컬럼1의 값, 컬럼2=컬럼2의 값
WHERE 대상이 될 컬럼명=컬럼의 값;
```

### 삭제 (DELETE)

행단위로 데이터를 삭제

```
DELETE FROM 테이블명 WHERE 삭제하려는 칼럼 명=값;
```

### TRUNCATE

테이블 전체 데이터를 삭제
테이블에 외부키(foreign key)가 없다면 DELETE보다 빠르게 삭제 가능

```
TRUNCATE 테이블명;
```

### DROP TABLE

테이블을 삭제

```
DROP TABLE 테이블명;
```
