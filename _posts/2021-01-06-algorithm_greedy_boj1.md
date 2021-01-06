---
title: "[ALGO] GREEDY ALGORITHM BOJ BRONZE"
categories: 
  - CS
last_modified_at: 2021-01-06 12:00:00
comments: true
use_math: true # MathJax On
---

### 14720번
문제 링크 : [BOJ 14720](https://www.acmicpc.net/problem/14720)

`code`
```py
n = int(input())
data= map(int, input().split())

first = 0
count = 0

for milk in data:
	if milk == (first % 3):
		count += 1
		first += 1
print(count)
```

### 11034번
문제 링크 : [BOJ 11034](https://www.acmicpc.net/problem/11034)

`code`
```py
while True:
    try:
        a,b,c = map(int, input().split())
        print(max(b-a-1,c-b-1))
    except:
        break
```
