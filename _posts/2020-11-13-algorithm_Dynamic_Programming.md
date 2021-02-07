---
title: "[ALGO] Dynamic Programming"
categories: 
  - CS
last_modified_at: 2020-11-13 12:00:00
comments: true
use_math: true # MathJax On
---

#### Dynamic Programming

- 한 번 계산한 결과값은 별도의 메모리에 저장하여 다시 계산하지 않도록 하는 알고리즘
- 다이나믹 프로그래밍은 다음의 조건을 만족할 때 사용가능
  - Optimal Substructure
    - 큰 문제를 작은 문제로 나눌 수 있으며 작은 문제의 답을 모아서 큰 문제를 해결할 수 있다
  - Overlapping Subproblem
    - 동일한 작은 문제를 반복적으로 해결해야 한다

#### 피보나치 수열
- 다이나믹 프로그래밍으로 효과적으로 계산할 수 있는 기본 예시
![피보나치](https://user-images.githubusercontent.com/62474292/104395236-a3b07e00-558b-11eb-9807-d47d16ce6f57.JPG)

- n번쨰 피보나치 수를 f(n)이라 할 때 4번째 피보나치 수 f(4)를 구하는 과정은 다음과 같다
![f_4](https://user-images.githubusercontent.com/62474292/104395238-a4e1ab00-558b-11eb-895c-9d4a3c4742c9.JPG)

`code`
```py
# 피보나치 함수를 재귀함수로 구현
def fibo(x):
  if x == 1 or x == 2:
    return 1
  return fibo(x-1) + fibo(x-2)
```
- 시간 복잡도 : O(2^N)
- f(30)을 계산하기 위해 약 10억가량의 연산을 수행해야 함
- 아래와 같이 f(2)가 여러 번 호출되는 것을 확인할 수 있다.
![피보_트리](https://user-images.githubusercontent.com/62474292/104395241-a612d800-558b-11eb-9a75-916b9d4ecb4b.JPG)

#### 피보나치 수열의 효율적인 해법
- 피보나치 수열은 다음의 다이나믹 프로그래밍의 사용 조건을 만족
  - 큰 문제를 작은 문제로 나눌 수 있다
  - 동일한 작은 문제를 반복적으로 해결한다
  
#### Memoization
- 메모이제이션은 다이나믹 프로그래밍을 구현하는 방법 중 하나이다
- 한 번 계산한 결과를 메모리 공간에 메모해두고 같은 식을 다시 호출하면 메모한 결과를 그대로 가져오는 
  - 같은 문제를 다시 호출하면 메모했던 결과를 그대로 가져온다
  - 값을 기록해 놓는다는 점에서 **캐싱(Caching)** 이라고도 함
- 한 번 구한 정보를 리스트에 저장하고 다이다닉 프로그래밍을 재귀적으로 수행하다가 같은 정보를 필요할 때는 이미 구한 정답을 그대로 리스트에서 가져오는 방식으로 구현

`code`
```py
# 한 번 계산된 결과를 메모이제이션(Memoization)하기 위한 리스트 초기화
d = [0] * 100

# 피보나치 함수(Fibonacci Function)를 재귀함수로 구현 (탑다운 다이나믹 프로그래밍)
def fibo(x):
    # 종료 조건(1 혹은 2일 때 1을 반환)
    if x == 1 or x == 2:
        return 1
    # 이미 계산한 적 있는 문제라면 그대로 반환
    if d[x] != 0:
        return d[x]
    # 아직 계산하지 않은 문제라면 점화식에 따라서 피보나치 결과 반환
    d[x] = fibo(x - 1) + fibo(x - 2)
    return d[x]

print(fibo(99))
```

#### 메모이제이션 동작 분석
- 이미 계산된 결과를 메모리에 저장하면 다음과 같이 색칠된 노드만 처리하게 된다.
![메모이제이션](https://user-images.githubusercontent.com/62474292/104401455-939e9b80-5597-11eb-90f8-1c3532be6869.JPG)

- 실제로 호출되는 함수에 대해서만 확인해 보면 다음과 같이 방문하게 된다.
![호출](https://user-images.githubusercontent.com/62474292/104401459-94cfc880-5597-11eb-9de9-4a71ae138d8a.JPG)

- 다이나믹 프로그래밍을 적용했을 때의 피보나치 수열 알고리즘의 시간복잡도 : 0(N)
  - f(1)을 구한 다음 그 값이 f(2)를 푸는 데 사용되고, f(2)의 값이 f(3)을 푸는 데 사용되는 방식이므로

`code`
```py
# 호출되는 함수 확인

# 한 번 계산된 결과를 메모이제이션(Memoization)하기 위한 리스트 초기화
d = [0] * 100

# 피보나치 함수(Fibonacci Function)를 재귀함수로 구현 (탑다운 다이나믹 프로그래밍)
def fibo(x):
    print('f(' + str(x) + ')', end=' ')
    # 종료 조건(1 혹은 2일 때 1을 반환)
    if x == 1 or x == 2:
        return 1
    # 이미 계산한 적 있는 문제라면 그대로 반환
    if d[x] != 0:
        return d[x]
    # 아직 계산하지 않은 문제라면 점화식에 따라서 피보나치 결과 반환
    d[x] = fibo(x - 1) + fibo(x - 2)
    return d[x]

fibo(6)
```
```
f(6) f(5) f(4) f(3) f(2) f(1) f(2) f(3) f(4)
```

- 위와 같이 재귀 함수를 이용하여 다이나믹 프로그래밍을 하는 방법을 큰 문제를 해결하기 위해 작은 문제를 호출한다고 하여 **Top-Down**방식이라고 한다
- 반면에 단순히 반복문을 이용하여 다이나믹 프로그래밍을 하는 방법을 작은 문제부터 차근차근 답을 도출한다고 하여 **Bottom-Up**방식이라고 한다

`code`
```py
# 반복문을 이용하여 피보나치 수열 구현

# 앞서 계산된 결과를 저장하기 위한 DP 테이블 초기화
d = [0] * 100

# 첫 번째 피보나치 수와 두 번째 피보나치 수는 1
d[1] = 1
d[2] = 1
n = 99

# 피보나치 함수(Fibonacci Function) 반복문으로 구현(보텀업 다이나믹 프로그래밍)
for i in range(3, n + 1):
    d[i] = d[i - 1] + d[i - 2]

print(d[n])
```

- 다이나믹 프로그래밍의 전형적인 형태는 Bottom-Up 방식
- 이 때 사용되는 결과 저장용 리스트는 'DP 테이블'이라고 부른다
- 문제를 푸는 첫 단계는 주어진 문제가 DP 유형임을 파악하는 것
- 특정한 문제를 완전 탐색 알고리즘으로 접근했을 때 시간이 오래 거리면 DP를 적용할 수 있는지, 해결하고자 하는 부분 문제들의 중복 여부를 체크!




#### 기본 예제 1
![1](https://user-images.githubusercontent.com/62474292/104384001-16156400-5574-11eb-854b-b7cd675b35ab.JPG)

`code`
```py

```

#### 기본 예제 2
![2](https://user-images.githubusercontent.com/62474292/104383998-16156400-5574-11eb-893f-2b95583fa25f.JPG)

`code`
```py

```

#### 기본 예제 3
![3](https://user-images.githubusercontent.com/62474292/104383997-157ccd80-5574-11eb-84e3-b072f346e9c3.JPG)

`code`
```py

```

#### 기본 예제 4
![4](https://user-images.githubusercontent.com/62474292/104383989-13b30a00-5574-11eb-8925-cd40dac31531.JPG)

`code`
```py

```
