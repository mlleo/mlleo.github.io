---
title: "[Web Backend] SQL Basic / JDBC "
categories: 
  - CS
tags:
  - BACKEND
last_modified_at: 2021-03-31 12:00:00
comments: true
use_math: true # MathJax On
---

#### SQL
- 데이터베이스에 있는 정보를 사용할 수 있도록 지원하는 언어
- 모든 DBMS에서 사용가능
- 대소문자는 따로 구별하지 않음 (단, 데이터의 대소문자는 구분)

#### TABLE 생성
- 스키마 : 데이터베이스의 테이블에 저장될 데이터의 구조와 형식을 정의
- 회원 정보를 저장할 수 있는 MEMBER_INFO_라는 테이블 생성 예제
```mysql
use exampledb;

CREATE TABLE MEMBER_INFO (
  idx         INT         NOT NULL    AUTO_INCREMENT,
  userid      VARCHAR(16) NOT NULL,
  username    VARCHAR(20),
  userpwd     VARCHAR(16),
  emailid     VARCHAR(20),
  emaildomain VARCHAR(50),
  joindate    TIMESTAMP   NOT NULL    DEFAULT current_timestamp,
  PRIMARY KEY (idx)
) ENGINE = InnoDB DEFAULT CHARSET=utf8;
```
#### Data Manipulation Language (DML)
- INSERT : 데이터베이스 객체에 데이터를 입력
- SELECT : 데이터베이스 객체에서 데이터를 조회
- UPDATE : 데이터베이스 객체에 데이터를 수정
- DELETE : 데이터베이스 객체에 데이터를 삭제

#### INSERT
- 생략이 가능한 FIELD
  - NULL이 허용된 컬럼
  - DEFAULT가 설정된 컬럼
  - AUTO INCREMENT가 설정된 컬럼

```mysql
INSERT INTO table_name
VALUES(col_val1, col_val2, col_val3, ..., col_valN);
```

```mysql
# 칼럼 순서가 기억이 안나는 경우 칼럼도 명시해줘서 첫번째 컬럼에 col_val1 저장
INSERT INTO table_name(col_name1, col_name2, ..., col_nameN)
VALUES(col_val1, col_val2, col_val3, ..., col_valN);
```

```mysql
# 여러 값을 하나의 쿼리로 INSERT 시키는 경우
INSERT INTO table_name(col_name1, col_name2, ..., col_nameN)
VALUES(col_val1, col_val2, col_val3, ..., col_valN)
      (col_val1, col_val2, col_val3, ..., col_valN);
```

#### UPDATE
- WHERE 절의 조건에 만족하는 레코드의 값을 변경
- WHERE 절을 생략하면 모든 데이터가 바뀜


```mysql
UPDATE table_name
SET col_name1 = col_val1, col_name2 = col_val2, col_name3 = col_val3, ... , col_nameN = col_valN
WHERE conditions;
```
#### DELETE
- WHERE 절의 조건에 만족하는 레코드의 값을 삭제
- WHERE 절을 생략하면 모든 데이터가 삭제됨


```mysql
DELETE from table_name
WHERE conditions;
```

#### SELECT
- 테이블 내에서 원하는 컬럼 데이터 검색

```mysql
# 모든 사원의 모든 정보 검색
SELECT * FROM table_name;
```

```mysql
# 모든 사원의 사번, 이름, 급여, 급여에 따른 등급 표시 검색
SELECT employee_id, first_name, salary,
       case when salary > 15000 then '고액연봉'
            when salary > 8000 then '평균연봉'
            else '저액연봉'
       end "연봉등급"
from employees;
```

```mysql
# 모든 회원의 모든 정보 검색
SELECT * FROM table_name;
```
