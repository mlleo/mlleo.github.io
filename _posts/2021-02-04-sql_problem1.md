---
title: "[SQL] PROBLEM SET 1"
categories: 
  - CS
last_modified_at: 2021-02-04 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 해커랭크입니다. (https://www.hackerrank.com/domains/sql)

#### 문제 1
![1](https://user-images.githubusercontent.com/62474292/106719766-09050580-6646-11eb-8cdc-1aa286eb4dce.JPG)

`code`
```sql
SELECT NAME
FROM CITY
WHERE POPULATION > 120000 AND COUNTRYCODE = 'USA';
```

#### 문제 2
![2](https://user-images.githubusercontent.com/62474292/106719772-0a363280-6646-11eb-96bb-40ec117d0090.JPG)

`code`
```sql
SELECT *
FROM CITY
```

#### 문제 3
![3](https://user-images.githubusercontent.com/62474292/106719773-0a363280-6646-11eb-9f29-a21266350917.JPG)

`code`
```sql
SELECT *
FROM CITY
WHERE ID = '1661';
```

#### 문제 4
![4](https://user-images.githubusercontent.com/62474292/106719774-0acec900-6646-11eb-95c1-be98df16dc37.JPG)

`code`
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

#### 문제 5
![5](https://user-images.githubusercontent.com/62474292/106719775-0acec900-6646-11eb-8fcd-b3dc6980993e.JPG)

`code`
```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

#### 문제 6
![6](https://user-images.githubusercontent.com/62474292/106719776-0b675f80-6646-11eb-9ea6-130afbffeed5.JPG)

`code`
```sql
SELECT CITY, STATE
FROM STATION;
```

#### 문제 7
![7](https://user-images.githubusercontent.com/62474292/106719794-0d312300-6646-11eb-99a3-77c72b9aa8db.JPG)

`code`
```sql
SELECT CITY
FROM STATION
WHERE MOD(ID,2) = 0
GROUP BY CITY;
```

#### 문제 8
![8](https://user-images.githubusercontent.com/62474292/106719796-0dc9b980-6646-11eb-94f2-aad3461f6c7d.JPG)

`code`
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION;
```

#### 문제 9
![9](https://user-images.githubusercontent.com/62474292/106719799-0e625000-6646-11eb-9926-b07dbf795bff.JPG)

`code`
```sql
SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY), CITY
LIMIT 1;

SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY
LIMIT 1
```

#### 문제 10
![10](https://user-images.githubusercontent.com/62474292/106719802-0e625000-6646-11eb-9652-41a76ba55c2e.JPG)

`code`
```sql
SELECT CITY
FROM STATION
WHERE (
    CITY LIKE 'E%'
    OR CITY LIKE 'A%'
    OR CITY LIKE 'I%'
    OR CITY LIKE 'O%'
    OR CITY LIKE 'U%'
    );
```
