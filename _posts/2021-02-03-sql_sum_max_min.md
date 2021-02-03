---
title: "[SQL] SUM,MAX,MIN"
categories: 
  - CS
last_modified_at: 2021-02-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 프로그래머스 SQL 고득점 KIT입니다. (https://programmers.co.kr/learn/challenges)

#### 예제 1
![1](https://user-images.githubusercontent.com/62474292/106706190-a48c7b00-6632-11eb-90e5-692449d76233.JPG)

`code`
```sql
SELECT DATETIME
FROM ANIMAL_INS
ORDER BY DATETIME DESC
LIMIT 1;
```

#### 예제 2
![2](https://user-images.githubusercontent.com/62474292/106706193-a5251180-6632-11eb-9c32-8f4356b164fc.JPG)

`code`
```sql
SELECT DATETIME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1;
```

#### 예제 3
![3](https://user-images.githubusercontent.com/62474292/106706195-a5bda800-6632-11eb-8539-b8421ef9acb7.JPG)

`code`
```sql
SELECT COUNT(*)
FROM ANIMAL_INS
```

#### 예제 4
![4](https://user-images.githubusercontent.com/62474292/106706196-a5bda800-6632-11eb-8bd7-c46fa9cbad88.JPG)

`code`
```sql
SELECT COUNT(DISTINCT NAME) AS count
FROM ANIMAL_INS;
```
