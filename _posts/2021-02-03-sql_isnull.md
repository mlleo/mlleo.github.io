---
title: "[SQL] ISNULL"
categories: 
  - CS
last_modified_at: 2021-02-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 프로그래머스 SQL 고득점 KIT입니다. (https://programmers.co.kr/learn/challenges)

#### 예제 1
![1](https://user-images.githubusercontent.com/62474292/106707741-14036a00-6635-11eb-9da3-341da5361e66.JPG)

`code`
```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME IS NULL
ORDER BY ANIMAL_ID
```

#### 예제 2
![2](https://user-images.githubusercontent.com/62474292/106707745-149c0080-6635-11eb-89dd-3772408e1655.JPG)

`code`
```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME IS NOT NULL
ORDER BY ANIMAL_ID
```

#### 예제 3
![3](https://user-images.githubusercontent.com/62474292/106707746-15349700-6635-11eb-89a6-0f6a1d91edb6.JPG)

`code`
```sql
SELECT ANIMAL_TYPE, IFNULL(NAME, "No name") AS NAME, SEX_UPON_INTAKE
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```
