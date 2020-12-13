---
title: "[ALGO] GREEDY ALGORITHM PROBLEM"
categories: 
  - CS
last_modified_at: 2020-10-16 12:00:00
comments: true
use_math: true # MathJax On
---

#### 문제1

![모험가길드](https://user-images.githubusercontent.com/62474292/100349922-7be17700-302c-11eb-94ff-ada05544449f.JPG)

`code`
```py
n = int(input())
stat = list(map(int, input().split()))
stat.sort()

group = 0

count = 0

for i in stat:
	count += 1
	if count >= i:
		group += 1
		count = 0

print(group)
```
#### 문제2
![곱하기혹은더하기](https://user-images.githubusercontent.com/62474292/100349936-7f74fe00-302c-11eb-962b-ac40dbad2bf6.JPG)

`code`
```py
data = input()
result = int(data[0])

for i in range(1,len(data)):
	num = int(data[i])
	if num<= 1 or result <=1:
		result += num
	else:
		result *= num

print(result)
```

#### 문제3
![문자열뒤집기](https://user-images.githubusercontent.com/62474292/100360584-72600b00-303c-11eb-8ad4-e73df2f4f297.JPG)

`code`
```py
s = input()

count0 = 0 
count1 = 0

if s[0]=='0':
    count1 += 1
else:
    count0 += 1

for i in range(len(s)-1):
    if s[i] != s[i+1]:
        if s[i+1]=='0':
            count1 += 1
        else:
            count0 += 1
print(min(count0,count1))
```

#### 문제4
![만들수없는금액](https://user-images.githubusercontent.com/62474292/100365437-d4237380-3042-11eb-81be-9f16e7cb2155.JPG)

`code`
```py
n = int(input())
coin = list(map(int, input().split()))
coin.sort()

target = 1
for i in data:
	if target < i:
		break
	target += i

print(target)
```

#### 문제5
![볼링공고르기](https://user-images.githubusercontent.com/62474292/100397105-723b2c00-308b-11eb-8cbc-f5db7156c688.JPG)

`code`
```py
n,m = map(int, input().split())
data = list(map(int, input().split()))

array = [0]*11

for x in data:
	array[x] += 1

result = 0

for i in range(1,m+1):
	n -= array[i]
	result += array[i] * n

print(result)
```

#### 문제6
![무지의먹방라이브](https://user-images.githubusercontent.com/62474292/102010627-992f7880-3d82-11eb-989d-b8e476180d40.JPG)
![무지의먹방라이브2](https://user-images.githubusercontent.com/62474292/102010624-97fe4b80-3d82-11eb-8ee2-f732501a4949.JPG)
![무지의먹방라이브3](https://user-images.githubusercontent.com/62474292/102010626-992f7880-3d82-11eb-9e23-8dea1baa02d1.JPG)

`code`
```py

```
<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
