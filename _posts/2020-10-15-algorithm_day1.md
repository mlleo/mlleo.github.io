---
title: "[ALGO] GREEDY ALGORITHM"
categories: 
  - CS
last_modified_at: 2020-10-15 12:00:00
comments: true
use_math: true # MathJax On
---

### 그리디 알고리즘

- 현재 상황에서 지금 당장 좋은 것만 고르는 방법
- 매 순간 가장 좋아보이는 것을 선택하며, 현재의 선택이 나중에 미칠 영향에 대해서는 고려하지 않음
- 기준에 따라 좋은 것을 선택하는 알고리즘이므로, 문제에서 **기준** 을 제시
- 주로 정렬 알고리즘과 함께 사용됨

#### 기본 예제1

![거스름돈](https://user-images.githubusercontent.com/62474292/100326241-0dd98780-300d-11eb-8d12-e12436d8cf28.JPG)

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
#### 기본 예제2 

![큰수의법칙](https://user-images.githubusercontent.com/62474292/100333796-59dcfa00-3016-11eb-87b2-4b3fb4ffb72e.JPG)

`code`

```py
n,m,k = map(int, input().split())
data = list(map(int, input().split()))

data.sort()

first = data[n-1]
second = data[n-2]

count = (m // (k+1)) * k
count += m % (k+1)

result = 0

result += count * first
result += (m-count) * second

print(result)
```
#### 기본 예제3

![숫자카드게임](https://user-images.githubusercontent.com/62474292/100333809-5d708100-3016-11eb-817d-587170b31a4c.JPG)

`code`
```py
n,m = map(int, input().split())

result = 0

for i in range(n):
	data = list(map(int, input().split()))
	min_value = min(data)
	result = max(result, min_value)

print(result)
```

#### 기본 예제4

![1이될때까지](https://user-images.githubusercontent.com/62474292/100335439-58143600-3018-11eb-980a-59c76c98954a.JPG)

`code`

```py
n, k = map(int, input().split())
result = 0

while True:
  target = (n // k) * k
  result += (n-target)
  n = target
  if n < k:
    break
  n //= k
  result +=1

result += (n-1)
print(result)
```

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)