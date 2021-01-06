---
title: "[ALGO] IMPLEMENTATION ALGORITHM BOJ BRONZE3"
categories: 
  - CS
last_modified_at: 2021-01-07 12:00:00
comments: true
use_math: true # MathJax On
---

### 11718번
문제 링크 : [BOJ 11718](https://www.acmicpc.net/problem/11718)

`code`
```py
while True:
	try:
		print(input())
	except:
		break
```

### 2741번
문제 링크 : [BOJ 2741](https://www.acmicpc.net/problem/2741)

`code`
```py
num = int(input())

for i in range(num):
    print(i+1)
```

### 2739번
문제 링크 : [BOJ 2739](https://www.acmicpc.net/problem/2739)

`code`
```py
a = int(input())
for i in range(1,10):
    print(f'{a} * {i} = {a*i}')
```

### 2438번
문제 링크 : [BOJ 2438](https://www.acmicpc.net/problem/2438)

`code`
```py
num = int(input())

for i in range(num):
    print("*"*(i+1))
```

### 10951번
문제 링크 : [BOJ 10951](https://www.acmicpc.net/problem/10951)

`code`
```py
while True:
    try:
        a,b = map(int, input().split())
        print(a+b)
    except:
        break
```

### 2439번
문제 링크 : [BOJ 2439](https://www.acmicpc.net/problem/2439)

`code`
```py
num = int(input())

for i in range(1,num+1):
    print(" "*(num-i)+"*"*i)
```

### 10817번
문제 링크 : [BOJ 10817](https://www.acmicpc.net/problem/10817)

`code`
```py
data = list(map(int,input().split()))
data.sort(reverse=True)
print(data[1])
```

### 10871번
문제 링크 : [BOJ 10871](https://www.acmicpc.net/problem/10871)

`code`
```py
n,x = map(int,input().split())
a = list(map(int,input().split()))

for i in range(n):
    if a[i]<x:
        print(a[i], end=" ")
```

### 2742번
문제 링크 : [BOJ 2742](https://www.acmicpc.net/problem/2742)

`code`
```py
num = int(input())

for i in range(num):
    print(num-i)
```

### 10818번
문제 링크 : [BOJ 10818](https://www.acmicpc.net/problem/10818)

`code`
```py
n = int(input())
a = list(map(int, input().split()))
print(min(a),max(a))
```
