---
title: "[ALGO] SORTING ALGORITHM BOJ BRONZE"
categories: 
  - CS
last_modified_at: 2021-01-07 12:00:00
comments: true
use_math: true # MathJax On
---

### 2752번
문제 링크 : [BOJ 2752](https://www.acmicpc.net/problem/2752)

`code`
```py
data = list(map(int, input().split()))
data.sort()
for num in data
	print(num, end=" ")
```

### 13771번
문제 링크 : [BOJ 13771](https://www.acmicpc.net/problem/13771)

`code`
```py
import sys

n= int(input())
arr = []

for _ in range(n):
	arr.append(float(sys.stdin.readline()))
arr.sort()
print("%.2f" %arr[1])
```

### 5576번
문제 링크 : [BOJ 5576](https://www.acmicpc.net/problem/5576)

`code`
```py
import sys

w = []
k = []

for i in range(20):
	if i < 10:
		w.append(int(sys.stdin.readline()))
	else:
		k.append(int(sys.stdin.readline()))
w.sort(reverse=True)
k.sort(reverse=True)

print(sum(w[:3]), sum(k[:3]))
```


### 15819번
문제 링크 : [BOJ 15819](https://www.acmicpc.net/problem/15819)

`code`
```py
import sys

n,l = map(int, input().split())
arr = []

for _ in range(n):
	arr.append(sys.stdin.readline())
arr.sort()
print(arr[l-1])

```


### 4631번
문제 링크 : [BOJ 4631](https://www.acmicpc.net/problem/4631)

`code`
```py
import sys

num = 1
while True:
	n = int(sys.stdin.readline())
	arr1 = []
	if n == 0:
		break
	for _ in range(n):
		arr1.append(sys.stdin.readline())
	arr2 = arr1[1::2]
	arr2 = reversed(arr2)
	arr1 = arr1[0::2]
	arr1.extend(arr2)
	print("SET %d" %num)
	num += 1
	for data in arr1:
		print(data, end="")
```

### 2750번
문제 링크 : [BOJ 2750](https://www.acmicpc.net/problem/2750)

`code`
```py
import sys

n = int(input())
arr = []

for _ in range(n):
    arr.append(int(sys.stdin.readline().rstrip()))  # rstrip() 안하면 개행문자도 같이 저장됨

for data in sorted(arr):
    print(data)

```

### 17224번
문제 링크 : [BOJ 17224](https://www.acmicpc.net/problem/17224)

`code`
```py
n,l,k = map(int, input().split())

sub1, sub2 = 0, 0
score = 0

for _ in range(n):
	easy, hard = map(int, input().split())
	if hard <= l:	# 어려운 문제 풀 수 있음
		sub2 += 1
	elif easy <= l :	# 쉬운 문제만 풀 수 있음
		sub1 += 1

score += 140 * min(sub2, k)
if sub2 < k:
	score += 100 * min(k-sub2,sub1)

print(score)

```




