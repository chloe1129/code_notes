## Table

데이터가 실질적으로 저장되는 저장소

### 스키마 (schema)

테이블에 적재될 데이터의 구조와 형식을 정의하는 것

```
CREATE TABLE table_name (
    `칼럼1` data_type,

    `칼럼2` tinyint NOT NULL,
    `name` char(4),
    `sex` enum(`male`, `female`),
    `address` varchar(50),
    `birthday` datetime,

    PRIMARY KEY (`칼럼1`)
)

# 테이블 리스트
SHOW tables;

# 테이블 스키마 열람
DESC `테이블명`

# 테이블 제거
    DROP TABLE `테이블명`

```
