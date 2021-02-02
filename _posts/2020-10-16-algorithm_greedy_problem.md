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

#### 문제1 풀이
- 공포도를 정렬한 후, 현재 확인하고 있는 공포도가 그룹 인원수보다 작거나 같으면 그룹 결성
- 단, 이 방식은 '모든 인원이 그룹을 형성해야 한다'라는 조건이 있으면 작동 안함 (이 경우 정렬을 내림차순으로 해서 풀어야 할 듯!)

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

#### 문제2 풀이
- 0이나 1이 아닌 이상 무조건 곱하기!

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

#### 문제3 풀이
- 0과 1이 연속에서 나오는 덩어리를 하나의 0,1로 취급한다.
- 예를 들어 0011000 의 경우 010으로 취급하고 이 경우 숫자가 바뀌는 구간 (count == 2)은 2번이고 이때의 최소 뒤집기 횟수는 1번이다.
- 0101, 01010, 010101 등 규칙을 찾아보면 최소 뒤집기 횟수를 찾아낼 수 있다.
- 010 : count = 2, result = 1
- 0101 : count = 3, result = 2
- 01010 : count = 4, result = 2
- 010101 : count = 5, result = 3
- 0101010 : count = 6, result = 3

`code`
```py
s = input()

count = 0

for i in range(len(s)-1):
    if s[i] != s[i+1]:
        count += 1
print((count+1)//2)
```

`code`
```py
# 책 모범답안
data = input()
count0 = 0  # 전부 0으로 바꾸는 경우
count1 = 0  # 전부 1로 바꾸는 경우

if data[0] =='1':
  count0 += 1
else:
  count1 += 1

for i in range(len(data)-1):
  if data[i] != data[i+1]:
    if data[i+1] == '1':
      count0 += 1
    else:
      count1 += 1
      
print(min(count0,count1))
````

#### 문제4
![만들수없는금액](https://user-images.githubusercontent.com/62474292/100365437-d4237380-3042-11eb-81be-9f16e7cb2155.JPG)

#### 문제4 풀이
- 1부터 (N-1)까지 만들 수 있다고 가정하면, 다음 동전이 N보다 큰 경우 금액 N을 만들지 못한다.
- 1부터 (N-1)까지 만들 수 있다고 가정했을 때, 다음 동전이 K이면 (N-1+K)까지는 만들 수 있다.

`code`
```py
n = int(input())
coin_list = list(map(int, input().split()))
coin_list.sort()

target = 1      # 만들 수 없는 최소 금액
for coin in coin_list:
	if target < coin:
		break
	target += coin

print(target)
```

#### 문제5
![볼링공고르기](https://user-images.githubusercontent.com/62474292/100397105-723b2c00-308b-11eb-8cbc-f5db7156c688.JPG)

#### 문제5 풀이
- 간단하게 생각하면 '전체 경우의 수 - 같은 무게로 만들어지는 경우의 수'를 구하면 된다
- 전체 경우의 수는 nC2
- 무게 별 개수를 파악하기 위해 배열에 빈도수를 계산
- 빈도수가 n이라면 같은 무게로 만들어지는 경우의 수는 nC2

`code`
```py
n,m = map(int, input().split())
k = list(map(int, input().split()))

k.sort()
tot = n*(n-1)//2        # 전체 경우의 수
arr = []                # 각각의 무게가 몇개씩 있는지 빈도수를 담을 배열
count = 0               # 빈도수
set = 0                 # 같은 무게로 만들어지는 경우의 수

for i in range(len(k)-1):
	count += 1
	if k[i] != k[i+1]:      # 무게가 달라지면 이전 무게의 총 빈도수를 배열에 저장
		arr.append(count)
		count = 0
arr.append(count+1)       # 마지막 무게의 총 빈도수를 배열에 저장
for i in arr:
	if i != 1:
		sub = i * (i-1) // 2
		set += sub

print(tot-set)
```

`code`
```py
# 인덱스를 활용해 빈도 구하는 과정 단순하게 한 코드

n,m = map(int, input().split())
k = list(map(int, input().split()))

tot = n*(n-1)//2

array = [0]*11

for x in k:
	array[x] += 1

set = 0


for i in array:
	if i != 1:
		sub = i * (i-1) // 2
		set += sub

print(tot-set)
```

`code`
```py
# 책 모범답안
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

#### 문제6 (프로그래머스 코드 참고)
![무지의먹방라이브](https://user-images.githubusercontent.com/62474292/102010627-992f7880-3d82-11eb-989d-b8e476180d40.JPG)
![무지의먹방라이브2](https://user-images.githubusercontent.com/62474292/102010624-97fe4b80-3d82-11eb-8ee2-f732501a4949.JPG)
![무지의먹방라이브3](https://user-images.githubusercontent.com/62474292/102010626-992f7880-3d82-11eb-9e23-8dea1baa02d1.JPG)

`code`
```py
def solution(food_times, k):
    answer = 0
    return answer
```
<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
