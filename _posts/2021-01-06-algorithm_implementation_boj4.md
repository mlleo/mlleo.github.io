---
title: "[ALGO] IMPLEMENTATION ALGORITHM BOJ BRONZE2"
categories: 
  - CS
last_modified_at: 2021-01-06 12:00:00
comments: true
use_math: true # MathJax On
---

### 1152번
문제 링크 : [BOJ 1152](https://www.acmicpc.net/problem/1152)

`code`
```py
s = input().split()
 
print(len(s))
```


### 15552번
문제 링크 : [BOJ 15552](https://www.acmicpc.net/problem/15552)

`code`
```py
import sys

num = int(input())
for i in range(num):
    a,b=map(int, sys.stdin.readline().split())
    print(a+b)
```


### 8958번
문제 링크 : [BOJ 8958](https://www.acmicpc.net/problem/8958)

`code`
```py
import sys

n = int(input())

for i in range(n):
    a = list(sys.stdin.readline())
    final_score = 0
    score = 1
    for j in a:
        if j =="O":
            final_score += score
            score += 1
        else:
            score=1
    print(final_score)
```


### 2562번
문제 링크 : [BOJ 2562](https://www.acmicpc.net/problem/2562)

`code`
```py
import sys

a=[]
for i in range(9):
	a.append(int(sys.stdin.readline()))
print(max(a))
print(a.index(max(a))+1)
```


### 10809번
문제 링크 : [BOJ 10809](https://www.acmicpc.net/problem/10809)

`code`
```py
from string import ascii_lowercase

s = list(input())
alpha_list = list(ascii_lowercase)

for alphabet in alpha_list:
	if alphabet in s:
		print(s.index(alphabet), end=" ")
	else:
		print("-1", end=" ")
```


### 15596번
문제 링크 : [BOJ 15596](https://www.acmicpc.net/problem/15596)

`code`
```py
def solve(a):
    ans = sum(a)
    return ans
```

### 2675번
문제 링크 : [BOJ 2675](https://www.acmicpc.net/problem/2675)

`code`
```py
import sys

t = int(input())

for _ in range(t):
    r, s = sys.stdin.readline().split()
    r = int(r)
    s = list(s)
    for data in s:
        print(str(data) * r, end="")
    print("")
```

### 11721번
문제 링크 : [BOJ 11721](https://www.acmicpc.net/problem/11721)

`code`
```py
n = list(input())

count = 0

for data in n:
    print(data, end="")
    count += 1

    if count % 10 == 0:
        print()

```

### 2920번
문제 링크 : [BOJ 2920](https://www.acmicpc.net/problem/2920)

`code`
```py
data = list(map(int, input().split()))

asc = sorted(data)
dec = sorted(data, reverse=True)

if data == asc:
	print("ascending")
elif data == dec:
	print("descending")
else:
	print("mixed")
```

### 2908번
문제 링크 : [BOJ 2908](https://www.acmicpc.net/problem/2908)

`code`
```py
a, b = input().split()

ans_a = 0
ans_b = 0

a = list(a)
b = list(b)
a.reverse()
b.reverse()

for i in range(3):
	ans_a += int(a[i]) * (10 ** (2-i))
	ans_b += int(b[i]) * (10 ** (2-i))

print(max(ans_a, ans_b))
```

