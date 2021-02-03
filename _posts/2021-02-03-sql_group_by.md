---
title: "[SQL] GROUP BY"
categories: 
  - CS
last_modified_at: 2021-02-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 프로그래머스 SQL 고득점 KIT입니다. (https://programmers.co.kr/learn/challenges)

#### 예제 1
![1](https://user-images.githubusercontent.com/62474292/106706584-3ac0a100-6633-11eb-908e-d3b07b2bfc06.JPG)
#### TIP
- 행의 개수를 알고 싶으면 COUNT(COLUMN_NAME) 사용!
- 

`code`
```sql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS count
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE;
```

#### 예제 2
![2](https://user-images.githubusercontent.com/62474292/106706586-3bf1ce00-6633-11eb-9e9b-bdc36f7d74f8.JPG)

`code`
```sql
SELECT NAME, COUNT
FROM (
    SELECT NAME, COUNT(NAME) AS COUNT
    FROM ANIMAL_INS
    GROUP BY NAME
    ) SQ1
WHERE COUNT >= 2 AND NAME IS NOT NULL
ORDER BY NAME;
```

#### 예제 3
![3](https://user-images.githubusercontent.com/62474292/106706588-3c8a6480-6633-11eb-8513-9f65614a2a40.JPG)

`code`
```sql
SELECT HOUR(DATETIME) AS HOUR, COUNT(DATETIME) AS COUNT
FROM ANIMAL_OUTS
WHERE HOUR(DATETIME) >= 9 AND HOUR(DATETIME) <= 19
GROUP BY HOUR(DATETIME)
ORDER BY HOUR
```

#### 예제 4
![4](https://user-images.githubusercontent.com/62474292/106706590-3c8a6480-6633-11eb-88fe-74b81515f3ca.JPG)

`code`
```sql

```
