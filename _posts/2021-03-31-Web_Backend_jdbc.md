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
- 테이블 내에서 원하는 컬럼 데이터 검색 (자세한 건 SQL 포스팅 참고!)

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
#### JDBC (Java DataBase Connectivity)
- 자바 프로그래밍 언어로 만들어진 클래스와 인터페이스로 이루어진 API
- SQL문을 실행할 수 있는 함수 호출 인터페이스
- DMBS 종류에 독립적인 자바 프로그래밍 가능
- 데이터베이스가 달라지더라도 동일한 API를 사용하게 해준다(드라이버 및 URL만 수정하면 가능)

#### JDBC 기능
- 데이터베이스에 연결 설정한다.
- SQL문을 DBMS에 전송한다.
- SQL문 전송 후 결과를 처리할 수 있게 해준다.

#### JDBC Interface
- 데이터베이스를 만드는 업체에게 제공되는 인터페이스
  - 업체에게 제공되는 인터페이스를 각각의 DBMS업체들이 구현해 놓은 것이 드라이버
- 프로그래머에게 제공되는 인터페이스
  - SQL 패키지가 제공하고 있는 라이브러리로서 프로그래머는 이 라이브러리를 기반으로 DB 프로그램을 작성할 수 있다

![JDBC](https://user-images.githubusercontent.com/62474292/113104919-01c03980-923c-11eb-9654-c0c78d04d318.JPG)

#### JDBC API : java.sql package
- Driver(interface)
  - 드라이버에 대한 정보를 가지고 있다.
  - 모든 드라이버가 반드시 구현해야 하는 인터페이스
  - 드라이버의 버전이나 연결에 대한 정보를 알아볼 수 있는 메소드를 가지고 있다.
  
- Connection (interface)
  - 데이터베이스에 대한 하나의 세션을 표현한다.
  - 세션은 하나의 클라이언트가 서버에 요청을 하기 위해 연결을 맺은 상태를 의미한다.
  - DriverManager 클래스의 getConnection() 메소드를 이용하여 얻어 올 수 있다.
  - default로 setAutoCommit(true)로 설정된다.
  - 개발자가 원하는 경우에 commit을 해주고 싶거나 transaction이 아주 중요한 부분에 있어서 RollBack 처리를 하고자 할 경우에는 setAutoCommit(false)로 설정한다.
  - 단, 이 경우에는 SQL문을 수행할 때 마다 명시적으로 commit()을 호출해야 한다.

- Statement (interface)
  - SQL문장을 실행하고 그것에 대한 결과 값을 가져오기 위해 사용한다.
  - public boolean execute(String sql) throws SQLException
    - 특별히 SQL문을 구분하지 않고 DML(delete, update, insert), Query(select), DDL(create, drop)등을 수행할 수 있다. 결과가 ResultSet이면 true이고 결과가 DML이거나 특별한 결과가 없으면 false를 리턴한다.
  - public ResultSet executeQuery(String sql) throws SQLException
    - Select를 처리할 때 사용한다
  - public int executeUpdate(String sql) throws SQLException
    - 주로 DML(delete, update, insert)등의 SQL을 수행할 때 사용한다.

- PreparedStatement (interface)
  - 동일한 SQL 문장이 여러 번 반복적으로 수행될 때 사용하는 객체
  - 대용량의 문자나 바이너리 타입의 데이터 (이미지나 사운드 등)를 저장하기 위해서도 사용될 수 있다
  - SQL 문장이 미리 컴파일되어 PreparedStatement 객체에 저장된다
  - 여러 번 반복 수행 시 clearParameters() 메소드를 이용해 Statement에 남겨진 값을 초기화한다.
  - public ResultSet executeQuery() throws SQLException
    - Select를 처리할 때 사용
  - public int executeUpdate() throws SQLException
    - 주로 DML(delete, update, insert)등의 SQL을 수행할 때 사용한다.

- CallableStatement (interface)
  - 데이터베이스에 대하여 실제 SQL문을 실행하는 것이 아니라 Stored Procedures를 호출한다.
  - Stored Procedures란 연속되는 SQL문으로 데이터베이스에 저장해 두고 마치 함수의 호출처럼 사용한다.
  - 데이터베이스에 Stored Procedures를 만들어두고 자바에서 호출하여 사용할 수 있게 한다.
  - Stored Procedures 사용 시 속도의 향상을 기대할 수 있고, 자바 코드에 SQL문장이 들어가지 않으므로 자바코드가 SQL에 독립적이게 된다.

- ResultSet (interface)
  - 쿼리에 대한 결과값 처리
  - ResultSet 객체의 커서는 첫번째 레코드보다 바로 이전을 가리킨다.
  - next() : ResultSet 객체의 커서를 이동
  - getXXX(index or name) 메소드를 이용하여 데이터를 얻을 수 있다. (ex. getString(index or name))

#### JDBC PROGRAMMING 개발 순서
1. JDBC Driver Loading
2. DBMS와 연결 (Connection 생성)
3. SQL 실행 준비 (Statement, PreparedStatement 생성)
4. SQL 실행 (DML : insert, update, delete, Query : select)
5. DBMS 연결 끊기

#### JDBC Driver Loading
- 데이터베이스와의 접속을 오픈하기 위해 어플리케이션의 JVM안으로 특정 드라이버 클래스를 적재
- Class.forName(Driver ClassName);
- 각 Database별 Driver class
  - MySQL : com.mysql.cj.jdbc.Driver
  - Oracle : oracle.jdbc.driver.OracleDriver
  - MSSQL : com.microsoft.sqlserver.jdbc.SQLServerDriver

#### DBMS와 연결 (Connection 생성)
- DriverManager 클래스를 이용하여 URL 형태로 주어진 데이터베이스에 대한 접속을 요청
- Connection con = DriverManager.getConnection(URL, dbid, dbpassword);
- JDBC URL은 드라이버 고유의 방식으로 개별적인 데이터베이스를 식별
  - MySQL : jdbc:mysql://IP:3306/DBNAME?characterEncoding=utf8&autoReconnect=true
  - Oracle : jdbc:oracle:thin:@IP:3306:DBNAME
  - MSSQL : jdbc:sqlserver://IP:3306;DatabaseName=DBNAME

#### SQL 실행 준비 (Statement, PreparedStatement 생성)
- String sql = "insert, update, delete, select, ...";
- Statement 생성 : Statement stmt = conn.createStatement();
- PreparedStatement 생성 : PreparedStatement pstmt = conn.prepareStatement(sql);

#### SQL 실행 (executeUpdate, executeQuery)
- Statement
  - DML : int cnt = stmt.executeUpdate(sql);
  - Select : ResultSet rs = stmt.executeQuery(sql);
- PreparedStatement
  - sql문의 치환변수 값 설정 : pstmt.setXXX(index, val);
  - DML : int cnt = pstmt.executeUpdate();
  - Select : ResultSet rs = pstmt.executeQuery();
- ResultSet
  - ResultSet을 얻어온 후 rs.next()를 실행해야 한다.
    - select의 결과가 반드시 하나가 나오는 경우 : rs.next();
    - select의 결과가 하나 또는 못 얻어 오는 경우 : if(rs.next){}
    - select의 결과가 여러 개가 나올 수 있는 경우 : while(rs.next()){}
  - 값 얻기
    - String str = rs.getString(index or name);
    - int cnt = rs.getInt(index or name);

#### DBMS 연결 끊기
- 모든 작업이 끝난 경우에는 ResultSet, Statement(PreparedStatement), Connection 객체의 close() 메소드를 이용하여 작업을 종료한다. (연결한 순의 역순으로 종료)
- Connection은 상당한 overhead를 가져온다. 따라서 최적화된 상태를 유지하기 위해서는 반드시 Connection을 닫아 주어야 한다.
  - rs.close();
  - pstmt.close();
  - conn.close();
