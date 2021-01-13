---
title: "[ALGO] Dynamic Programming"
categories: 
  - CS
last_modified_at: 2020-11-13 12:00:00
comments: true
use_math: true # MathJax On
---

#### Dynamic Programming
- 한 번 계산한 문제는 다시 계산하지 않도록 하는 알고리즘
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
- 피보나치 수열은 다음의 다이나믹 프로그램잉의 사용 조건을 만족
  - 큰 문제를 작은 문제로 나눌 수 있다
  - 동일한 작은 문제를 반복적으로 해결한다
  
#### Memoization
- 메모이제이션은 다이나믹 프로그래밍을 구현하는 방법 중 하나이다
- 한 번 계산한 결과를 메모리 공간에 메모하는 기법이다










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
