---
title: "[ALGO] GREEDY ALGORITHM"
categories: 
  - CS
tags:
  - ALGORITHM
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

#### 예제1 풀이
- 가장 큰 금액부터 거슬러 줄 수 있는 만큼 거슬러 주자!
- 화폐 단위를 리스트로 만들고 큰 금액부터 최대한 거슬러 주면서 count 증가!
- 큰 단위가 작은 단위의 배수 형태가 아니라면 그리디 알고리즘으로 풀 수 없음! (DP로 풀어야 함!)

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

#### 예제2 풀이
- 결국 가장 큰 수와 두 번째로 큰 수만 찾으면 된다!
- (가장 큰 수 * k번 + 두 번째로 큰 수 * 1번)을 하나의 그룹으로 생각!
- 가장 큰 수가 몇 번 나올지를 계산하면 자연스럽게 두 번째로 큰 수는 m에서 계산된 값을 빼주면 됨!

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

#### 예제3 풀이
- 각 행별로 최소인 카드값을 기억
- 이 중에서 최대값을 찾는 문제이므로 max 함수 이용!
- 아래 풀이와 별도로 리스트에 행별 최솟값 기록한 다음 max 해도 됨!

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

#### 예제4 풀이
- n이 1보다 큰 경우 나눗셈이 무조건 좋음(n = 2 인 경우라도 동일한 성능)
- repeat
- n이 k로 나눠지는 target 숫자를 찾자!
- 그 전까지 -1 연산을 통해 count 증가!
- target 숫자가 되면 n을 k로 나누고 count 증가
- repeat end
- n이 k보다 작아지면, 이때부터는 1이 될까지 -1 연산을 통해 count 증가!

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

`code`

```py
# 직관적인 풀이
n, k = map(int, input().split())        # n : 입력 자연수, k: 나누는 수

count = 0
while True:
    if n < k:
        break
    if n % k != 0:
        count += (n % k)
        n -= (n % k)
    else:
        count += 1
        n //= k

count += (n-1)
print(count)
```
<br><br>

[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
