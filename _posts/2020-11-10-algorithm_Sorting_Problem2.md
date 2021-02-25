---
title: "[ALGO] Sorting PROBLEM 2"
categories: 
  - CS
last_modified_at: 2020-11-10 12:00:00
comments: true
use_math: true # MathJax On
---

#### 문제 1
![국영수](https://user-images.githubusercontent.com/62474292/101992899-b4a27100-3cf9-11eb-8ef6-bdd53f433e3c.JPG)

#### 문제 1 풀이
- 기본적인 정렬 문제이지만 정렬 조건이 순차적으로 여러개라는 점만 주의하면 된다!
- 람다 함수를 통해 정렬 조건 순차적으로 명시!

`code`
```py
n = int(input())            # 학생 수
data = []
for _ in range(n):
    data.append(list(input().split()))

arr = sorted(data, key= lambda x : (-int(x[1]), int(x[2]), -int(x[3]), x[0]))

for i in range(n):
    print(arr[i][0])
```

#### 문제 2
![안테나](https://user-images.githubusercontent.com/62474292/101992900-b53b0780-3cf9-11eb-8362-04a1c1c9f15d.JPG)

#### 문제 2 풀이
- 완전탐색으로도 해결할 수 있지만 시간초과
- 타겟이 될 만한 집을 골라야 하는데 이 때 집의 위치를 전부 정렬시켰을 때 중앙에 있는 집이 타겟으로 적합!
- 집 개수가 홀수, 짝수일때 모두를 고려하기 위해 안정성 있게 타겟을 2개 설정(짝수일 때는 중앙이라고 할 수 있는 타겟이 2개!)
- 완전탐색 O(N^2)에서 시간복잡도가 O(N)으로 줄어듬!

`code`
```py
import sys

n = int(input())            # 집 개수
pos = list(map(int, input().split()))       # 집 위치
pos.sort()
mid = len(pos)//2
target_list = [pos[mid-1], pos[mid]]

min_value = sys.maxsize
result = 0

for target in target_list:
    sum = 0
    for j in range(len(pos)):
        sum += abs(target-pos[j])
    if min_value > sum:
        result = target
        min_value = sum

print(result)
```

#### 문제 3 (프로그래머스 코드 참고)
![실패율](https://user-images.githubusercontent.com/62474292/101992898-b409da80-3cf9-11eb-8bff-0faea5e5f1e6.JPG)
![실패율2](https://user-images.githubusercontent.com/62474292/101992897-b409da80-3cf9-11eb-8459-874b37874cfa.JPG)
![실패율3](https://user-images.githubusercontent.com/62474292/101992896-b3714400-3cf9-11eb-9356-9270d8cdab38.JPG)

`code`
```py

```

#### 문제 4
![카드정렬하기](https://user-images.githubusercontent.com/62474292/101992894-b2401700-3cf9-11eb-998c-0dfbc864ee33.JPG)

`code`
```py

```
<br><br>
[출처] 이것이 취업을 위한 코딩 테스트다 with 파이썬 (나동빈 지음)
