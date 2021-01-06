---
title: "[ALGO] IMPLEMENTATION ALGORITHM BOJ BRONZE4"
categories: 
  - CS
last_modified_at: 2021-01-07 12:00:00
comments: true
use_math: true # MathJax On
---

### 1008번
문제 링크 : [BOJ 1000](https://www.acmicpc.net/problem/1008)

`code`
```py
a,b=map(int, input().split())
print(a/b)
```

### 9498번
문제 링크 : [BOJ 9498](https://www.acmicpc.net/problem/9498)

`code`
```py
a=int(input())
if a>=90:
    print("A")
elif a>=80:
    print("B")
elif a>=70:
    print("C")
elif a>=60:
    print("D")
else:
    print("F")
```

### 1330번
문제 링크 : [BOJ 1000](https://www.acmicpc.net/problem/1330)

`code`
```py
a,b=map(int, input().split())
if(a>b):
    print(">")
elif(a<b):
    print("<")
else:
    print("==")
```

### 2753번
문제 링크 : [BOJ 2753](https://www.acmicpc.net/problem/2753)

`code`
```py
year= int(input())

if year % 4 == 0 and (year % 100 != 0 or year % 400 == 0):
	print("1")
else:
	print("0")
```

### 14681번
문제 링크 : [BOJ 14681](https://www.acmicpc.net/problem/14681)

`code`
```py
a,b = map(int, input().split())

if a>0 and b>0:
    print("1")
elif a<0 and b>0:
    print("2")
elif a<0 and b<0:
    print("3")
else:
    print("4")
```

### 1008번
문제 링크 : [BOJ 1000](https://www.acmicpc.net/problem/1008)

`code`
```py
a,b=map(int, input().split())
print(a/b)
```

### 1212번
문제 링크 : [BOJ 1212](https://www.acmicpc.net/problem/1212)

`code`
```py
print(bin(int(input(),8))[2:])
```

### 10101번
문제 링크 : [BOJ 10101](https://www.acmicpc.net/problem/10101)

`code`
```py
a = int(input())
b = int(input())
c = int(input())

if a+b+c != 180:
	print("Error")
elif a == b and b == c:
	print("Equilateral")
elif a == b or b == c or a == c:
	print("Isosceles")
else:
	print("Scalene")
```

### 2420번
문제 링크 : [BOJ 2420](https://www.acmicpc.net/problem/2420)

`code`
```py
n,m = map(int,input().split())
print(abs(n-m))
```

### 10797번
문제 링크 : [BOJ 10797](https://www.acmicpc.net/problem/10797)

`code`
```py
day = int(input())
car = list(map(int,input().split()))

count = 0

for i in range(len(car)):
	if car[i] == day:
		count += 1
print(count)
```

### 10162번
문제 링크 : [BOJ 10162](https://www.acmicpc.net/problem/10162)

`code`
```py
t = int(input())

result = 0

min_div = t // 10

num_A = min_div // 30
num_B = (min_div - num_A * 30) // 6
num_C = (min_div - num_A * 30 - num_B * 6) 

if t % 10 != 0:
	print("-1")

else:
	print(str(num_A) + " " + str(num_B)+ " " + str(num_C))
```
