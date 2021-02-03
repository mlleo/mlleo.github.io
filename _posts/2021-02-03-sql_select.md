---
title: "[SQL] SELECT"
categories: 
  - CS
last_modified_at: 2021-02-03 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 프로그래머스 SQL 고득점 KIT입니다. (https://programmers.co.kr/learn/challenges)

#### 예제 1
![1](https://user-images.githubusercontent.com/62474292/106705610-a3a71980-6631-11eb-8548-57b1b81ebc6d.JPG)

`code`
```sql
SELECT * 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID
```


#### 예제 2
![2](https://user-images.githubusercontent.com/62474292/106705614-a4d84680-6631-11eb-89d5-849f51264f29.JPG)

`code`
```sql
SELECT NAME, DATETIME 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID DESC
```
#### 예제 3
![3](https://user-images.githubusercontent.com/62474292/106705615-a4d84680-6631-11eb-96e7-27c958155a66.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
WHERE INTAKE_CONDITION = 'Sick' 
ORDER BY ANIMAL_ID
```
#### 예제 4
![4](https://user-images.githubusercontent.com/62474292/106705618-a570dd00-6631-11eb-8005-484674b33421.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
WHERE NOT INTAKE_CONDITION ='Aged' 
ORDER BY ANIMAL_ID
```
#### 예제 5
![5](https://user-images.githubusercontent.com/62474292/106705619-a570dd00-6631-11eb-81b4-0c6839a034d6.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
ORDER BY ANIMAL_ID
```
#### 예제 6
![6](https://user-images.githubusercontent.com/62474292/106705621-a6097380-6631-11eb-998c-11673e7d96b9.JPG)

`code`
```sql
SELECT ANIMAL_ID, NAME, DATETIME 
FROM ANIMAL_INS 
ORDER BY NAME, DATETIME DESC
```
#### 예제 7
![7](https://user-images.githubusercontent.com/62474292/106705623-a6097380-6631-11eb-8f55-29e1601f2297.JPG)

`code`
```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```
