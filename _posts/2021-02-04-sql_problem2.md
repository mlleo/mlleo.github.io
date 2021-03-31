---
title: "[SQL] PROBLEM SET 2"
categories: 
  - CS
tags:
  - SQL
last_modified_at: 2021-02-04 12:00:00
comments: true
use_math: true # MathJax On
---

#### 모든 문제의 출처는 해커랭크입니다. (https://www.hackerrank.com/domains/sql)

#### 문제 1
![1](https://user-images.githubusercontent.com/62474292/106748687-f05a1700-6668-11eb-82cc-465968f29798.JPG)

`code`
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '%a'
      OR CITY LIKE '%e'
      OR CITY LIKE '%i'
      OR CITY LIKE '%o'
      OR CITY LIKE '%u';
```

#### 문제 2
![2](https://user-images.githubusercontent.com/62474292/106748694-f18b4400-6668-11eb-84bb-daf24f4205f1.JPG)

`code`
```sql
SELECT CITY
FROM STATION
WHERE LEFT(CITY,1) IN ('a','e','i','o','u') AND RIGHT(CITY,1) IN ('a','e','i','o','u');
```

#### 문제 3
![3](https://user-images.githubusercontent.com/62474292/106748695-f18b4400-6668-11eb-9d24-042e865947bc.JPG)

`code`
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE NOT LEFT(CITY,1) IN ('a','e','i','o','u'); 
```

#### 문제 4
![4](https://user-images.githubusercontent.com/62474292/106748698-f223da80-6668-11eb-9da2-9d4edce05a04.JPG)

`code`
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE NOT RIGHT(CITY,1) IN ('a','e','i','o','u');
```

#### 문제 5
![5](https://user-images.githubusercontent.com/62474292/106748699-f223da80-6668-11eb-8cb7-d92db141c789.JPG)

`code`
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE NOT LEFT(CITY,1) IN ('a','e','i','o','u') OR NOT RIGHT(CITY,1) IN ('a','e','i','o','u');
```

#### 문제 6
![6](https://user-images.githubusercontent.com/62474292/106748701-f2bc7100-6668-11eb-9c2b-0df4683c7f0c.JPG)

`code`
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE NOT LEFT(CITY,1) IN ('a','e','i','o','u') AND NOT RIGHT(CITY,1) IN ('a','e','i','o','u');
```

#### 문제 7
![7](https://user-images.githubusercontent.com/62474292/106748706-f3550780-6668-11eb-93a4-39d7466bec2d.JPG)

`code`
```sql
SELECT NAME
FROM STUDENTS
WHERE MARKS > 75
ORDER BY RIGHT(NAME,3), ID;
```

#### 문제 8
![8](https://user-images.githubusercontent.com/62474292/106748709-f3ed9e00-6668-11eb-936d-76f01dcb3e9d.JPG)

`code`
```sql
SELECT NAME
FROM Employee
ORDER BY NAME;
```

#### 문제 9
![9](https://user-images.githubusercontent.com/62474292/106748710-f3ed9e00-6668-11eb-9e40-4765943e31d0.JPG)

`code`
```sql
SELECT name
FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;
```

#### 문제 10
![10-1](https://user-images.githubusercontent.com/62474292/106748711-f4863480-6668-11eb-9a01-b7362c59e67b.JPG)
![10-2](https://user-images.githubusercontent.com/62474292/106748715-f4863480-6668-11eb-9752-57f2495f7b63.JPG)

`code`
```sql

```
