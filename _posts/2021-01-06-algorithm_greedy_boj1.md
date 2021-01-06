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

### 2810번
문제 링크 : [BOJ 2810](https://www.acmicpc.net/problem/2810)

`code`
```py
n = int(input())
data = input()

couple = data.count('LL')

if couple <= 1:
    print(n)
else:
    print(n+1-couple)
```

### 5585번
문제 링크 : [BOJ 5585](https://www.acmicpc.net/problem/5585)

`code`
```py
n = int(input())
change = 1000-n
count = 0
coin_list = [500,100,50,10,5,1]

for coin in coin_list:
	count +=  change // coin
	change %= coin

print(count)
```

### 2839번
문제 링크 : [BOJ 2839](https://www.acmicpc.net/problem/2839)

`code`
```py
n = int(input())

result = 0
 
while True:
    if (n % 5) == 0:
        result += n // 5
        break
    else:
        n -= 3
        result += 1
        if n == 0:
            break
       
        if n < 0:
            result = -1
            break
print(result)
```
### 15904번
문제 링크 : [BOJ 15904](https://www.acmicpc.net/problem/15904)

`code`
```py
s = list(input())

opt = 0

for i in range(len(s)):
	if opt == 0 and s[i] == 'U':
		opt = 1
	if opt == 1 and s[i] == 'C':
		opt = 2
	if opt == 2 and s[i] == 'P':
		opt = 3
	if opt == 3 and s[i] == 'C':
		opt = 4
if opt == 4:
	print("I love UCPC")
else:
	print("I hate UCPC")
```

### 2828번
문제 링크 : [BOJ 2828](https://www.acmicpc.net/problem/2828)

`code`
```py
n,m = map(int, input().split())
j = int(input())

front = 1
back = m

result = 0

for _ in range(j):
	data = int(input())
	if data < front:
		move = front-data
		front -= move
		back -= move
		result += move
	elif front <= data and data <= back:
		continue
	else:
		move = data-back
		front += move
		back += move
		result += move

print(result)
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
