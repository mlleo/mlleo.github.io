---
title: "[SQL] STRING, DATE"
categories: 
  - CS
tags:
  - SQL
last_modified_at: 2021-02-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 프로그래머스 SQL 고득점 KIT입니다. (https://programmers.co.kr/learn/challenges)

#### 예제 1
![1](https://user-images.githubusercontent.com/62474292/106708525-5da08480-6636-11eb-9c78-c82cf0fdbbd4.JPG)

#### TIP
- IN : WHERE 절 내에서 여러 값을 설정하고자 할 때 사용
  - WHERE COLUMN_NAME IN (Value1, Value2, Value3)
- BETWEEN : WHERE 절 내에서 검색 조건으로 범위를 지정하고자 할 때 사용 (이상, 이하 개념)
  - WHERE COLUMN_NAME BETWEEN Value1 AND Value2

`code`
```sql
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
FROM ANIMAL_INS
WHERE NAME in ('Lucy','Ella','Pickle','Rogan','Sabrina', 'Mitty')
ORDER BY ANIMAL_ID
```

#### 예제 2
![2](https://user-images.githubusercontent.com/62474292/106708528-5ed1b180-6636-11eb-815c-429f01a13365.JPG)

#### TIP
- LIKE : WHERE 절과 함게 특정 패턴을 검색할 때 사용
  - % : 0개 문자, 혹은 여러 개의 문자를 의미
  - _ : 하나의 문자를 의미
  - LIKE 'a%' : a로 시작되는 모든 문자열
  - LIKE 'a__%' : a로 시작되고 최소 3이상의 길이를 가진 문자열
  - LIKE '_ r%' : 두 번째 자리에 r이 들어가는 모든 문자열

`code`
```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE NAME LIKE '%EL%' AND ANIMAL_TYPE = 'Dog'
ORDER BY NAME
```

#### 예제 3
![3](https://user-images.githubusercontent.com/62474292/106708530-5ed1b180-6636-11eb-9d5c-3eeb31f81c5c.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME, CASE
WHEN SEX_UPON_INTAKE LIKE '%Neutered%'OR SEX_UPON_INTAKE LIKE '%Spayed%' THEN 'O' 
ELSE 'X' 
END AS "중성화"
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```

#### 예제 4
![4-1](https://user-images.githubusercontent.com/62474292/106708531-5f6a4800-6636-11eb-95d3-9842cadbf3f0.JPG)
![4-2](https://user-images.githubusercontent.com/62474292/106708533-5f6a4800-6636-11eb-9df8-095f44629c86.JPG)

#### TIP
- DATE타입끼리는 기본적인 사칙연산 가능!

`code`
```sql
SELECT INS.ANIMAL_ID, INS.NAME
FROM ANIMAL_INS AS INS INNER JOIN ANIMAL_OUTS AS OUTS
ON INS.ANIMAL_ID = OUTS.ANIMAL_ID
ORDER BY OUTS.DATETIME-INS.DATETIME DESC
LIMIT 2
```

#### 예제 5
![5](https://user-images.githubusercontent.com/62474292/106708534-6002de80-6636-11eb-8a7d-e60cfb3ac8b9.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, "%Y-%m-%d") AS 날짜
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```
