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
